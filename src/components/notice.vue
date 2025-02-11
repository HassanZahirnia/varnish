<template>
    <div v-if="display"
         class="varnish-notice varnish-font">

        <!-- Container -->
        <div class="varnish-container border rounded-md relative"
             :class="[modes[mode][type].border, `varnish-${type}`]">

            <!-- Tab -->
            <span v-if="format === 'tab'"
                  :class="modes[mode][type].tab"
                  class="varnish-tab absolute top-0 left-3 rounded-b font-[650] text-[9.5px] text-white dark:text-gray-300 uppercase tracking-wider px-2 pt-[3px] pb-1">

                <!-- Text -->
                {{ type }}

            </span>

            <!-- Content -->
            <div :class="[modes[mode][type].content, format === 'tab' ? 'px-5 pt-8 pb-4' : 'px-5 py-4']"
                 class="varnish-content rounded-md font-medium flex items-center -tracking-[.2px]">

                <!-- Icon -->
                <i v-if="format === 'icon'"
                   :class="modes[mode][type].icon"
                   class="varnish-icon fas text-[26px] opacity-[.50] ml-1 mr-[22px]">
                </i>

                <!-- Value -->
                <div class="leading-normal relative"
                     :class="format === 'tab' ? '' : 'top-[1px]'">

                    <!-- Text -->
                    {{ value }}

                </div>

            </div>

            <!-- Dismiss -->
            <i v-if="dismiss"
               @click="hide()"
               title="Hide this notice"
               class="varnish-dismiss fas fa-times text-gray-400 dark:text-gray-500 hover:text-gray-600 dark:hover:text-gray-400 absolute top-3 right-3 transition duration-300 cursor-pointer">
            </i>

        </div>

    </div>
</template>

<script>
    import Utilities from '../mixins/Utilities';

    export default
    {
        /**
         * Define the mixins.
         *
         */
        mixins : [
            Utilities,
        ],

        /**
         * Define the data model.
         *
         */
        data() { return {
            display : true,
            modes   : {
                opaque : {
                    danger : {
                        border  : 'border-red-600/[.40] dark:border-none',
                        content : 'bg-red-500/[.05] dark:bg-red-700/[.30] text-red-700/[.90] dark:text-red-300',
                        icon    : 'fa-circle-exclamation',
                        tab     : 'bg-red-600/[.40] dark:bg-red-700/[.30]',
                    },
                    info : {
                        border  : 'border-sky-600/[.40] dark:border-none',
                        content : 'bg-sky-500/[.05] dark:bg-sky-700/[.30] border-sky-500 text-sky-700/[.90] dark:text-blue-300',
                        icon    : 'fa-circle-info',
                        tab     : 'bg-sky-600/[.40] dark:bg-sky-700/[.30]',
                    },
                    success : {
                        border  : 'border-emerald-600/[.40] dark:border-none',
                        content : 'bg-emerald-500/[.05] dark:bg-emerald-700/[.30] text-emerald-700/[.90] dark:text-emerald-400',
                        icon    : 'fa-check-circle',
                        tab     : 'bg-emerald-600/[.40] dark:bg-emerald-700/[.30]',
                    },
                    warning : {
                        border  : 'border-yellow-600/[.40] dark:border-none',
                        content : 'bg-yellow-500/[.05] dark:bg-yellow-700/[.30] text-yellow-700 dark:text-orange-300',
                        icon    : 'fa-triangle-exclamation',
                        tab     : 'bg-yellow-600/[.40] dark:bg-yellow-700/[.30]',
                    },
                },
                transparent : {
                    danger : {
                        content : 'bg-transparent text-red-700 dark:text-red-300',
                        border  : 'border-red-500/[.40] dark:border-red-700/[.60]',
                        tab     : 'bg-red-600/[.40]',
                        icon    : 'fa-circle-exclamation',
                    },
                    info : {
                        border  : 'border-sky-600/[.40] dark:border-sky-700/[.60]',
                        content : 'bg-transparent text-sky-700 dark:text-blue-300',
                        icon    : 'fa-circle-info',
                        tab     : 'bg-sky-600/[.40]',
                    },
                    success : {
                        border  : 'border-emerald-600/[.40] dark:border-emerald-700/[.60]',
                        content : 'bg-transparent text-emerald-700 dark:text-emerald-400',
                        icon    : 'fa-check-circle',
                        tab     : 'bg-emerald-600/[.40]',
                    },
                    warning : {
                        border  : 'border-yellow-600/[.40] dark:border-yellow-700/[.60]',
                        content : 'bg-transparent text-yellow-700 dark:text-orange-300',
                        icon    : 'fa-triangle-exclamation',
                        tab     : 'bg-yellow-600/[.40]',
                    },
                }
            },
        }},

        /**
         * Define the public properties.
         *
         */
        props : {
            'dismiss' : { type : Boolean, default : false },
            'format'  : { type : String,  default : 'tab' },
            'id'      : { type : String,  default : '' },
            'mode'    : { type : String,  default : 'opaque' },
            'type'    : { type : String,  default : 'info' },
            'value'   : { type : String,  default : '' },
        },

        /**
         * Execute actions when the component is instantiated.
         *
         */
        created()
        {
            this.display = ! localStorage.getItem(`varnish_hide_notice_${this.id}`);
        },

        /**
         * Define the supporting methods.
         *
         */
        methods :
        {
            /**
             * Dismiss the notice from appearing again.
             *
             */
            hide()
            {
                if (! this.dismiss) return;

                this.display = false;

                localStorage.setItem(`varnish_hide_notice_${this.id}`, 1);
            }
        },
    }
</script>