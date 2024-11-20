<script lang="ts">
  import { getContext } from 'svelte';
  import { toast } from 'svelte-sonner';

  // Data and functions
  const i18n = getContext('i18n');

  let systemOverview = {
    uptime: '15 days, 4 hours, 37 minutes',
    cpuUsage: 55,
    memoryUsage: {
      percent: 70,
      used: '8 GB',
      total: '16 GB',
    },
    diskUsage: {
      percent: 85,
      used: '850 GB',
      total: '1 TB',
    },
  };

  let alerts = {
    critical: [
      'High Disk Usage: Disk usage has reached 85%, approaching capacity.',
      'Memory Usage Warning: Memory usage has exceeded 70%.',
    ],
    warnings: [
      'CPU Spike Detected: CPU usage spiked above 90% in the last hour.',
    ],
  };

  const downloadLog = (type: string) => {
    toast.success(`${i18n.t('Downloading')} ${type}...`);
    // Simulate download
    console.log(`Downloading ${type}...`);
  };
</script>


<div class="container">
    <div class="mb-3 text-sm font-bold">{$i18n.t('System Overview')}</div>
    <div class="section">
        <div class=" self-center text-xs font-medium">{$i18n.t('Uptime')}:{systemOverview.uptime}</div>
        <div class=" self-center text-xs font-medium">{$i18n.t('CPU Usage')}:{systemOverview.cpuUsage}%</div>
        <div class=" self-center text-xs font-medium">{$i18n.t('Memory Usage')}:{systemOverview.memoryUsage.percent}% 
            ({systemOverview.memoryUsage.used} of {systemOverview.memoryUsage.total}) </div>
        <div class=" self-center text-xs font-medium">{$i18n.t('Disk Usage')}:{systemOverview.diskUsage.percent}% 
            ({systemOverview.diskUsage.used} of {systemOverview.diskUsage.total})</div>
    </div>

    <hr class=" dark:border-gray-850 my-2" />

    <div class="mb-3 text-sm font-bold">{$i18n.t('Active Alerts')}</div>
    <div class="section">
    <div class=" self-center text-xs font-medium">
        {$i18n.t('Critical Alerts')}: 
      <ul class="alert-list">
        {#each alerts.critical as alert}
          <li>{alert}</li>
        {/each}
      </ul>
    </div> <br>
    <div class=" self-center text-xs font-medium">
        {$i18n.t('Warnings')}: 
      <ul class="alert-list">
        {#each alerts.warnings as warning}
          <li>{warning}</li>
        {/each}
      </ul>
    </div>
</div>

<hr class=" dark:border-gray-850 my-2" />

<script lang="ts">
  import { getContext } from 'svelte';
  import { toast } from 'svelte-sonner';

  // Data and functions
  const i18n = getContext('i18n');

  const downloadLog = (type: string) => {
    toast.success(`${i18n.t('Downloading')} ${type}...`);
    console.log(`Downloading ${type}...`);
  };
</script>

<style>
  .button-container {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .download-button {
    display: flex;
    align-items: center;
    gap: 8px;
    background: transparent;
    border: none;
    color: #333;
    font-size: 1rem;
    cursor: pointer;
    text-align: left;
    padding: 5px 0;
    width: fit-content;
  }

  .download-button svg {
    width: 16px;
    height: 16px;
    fill: #333;
  }

  .download-button:hover {
    color: #0056b3;
  }

  .download-button:hover svg {
    fill: #0056b3;
  }
</style>

<div class="button-container">
    <button
        type="button"
        class=" flex rounded-md py-2 px-3 w-full hover:bg-gray-200 dark:hover:bg-gray-800 transition"
        on:click={async () => {
            document.getElementById('config-json-input').click();
        }}
        >
        <div class=" self-center mr-3">
            <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 16 16"
                fill="currentColor"
                class="w-4 h-4"
            >
                <path d="M2 3a1 1 0 0 1 1-1h10a1 1 0 0 1 1 1v1a1 1 0 0 1-1 1H3a1 1 0 0 1-1-1V3Z" />
                <path
                    fill-rule="evenodd"
                    d="M13 6H3v6a2 2 0 0 0 2 2h6a2 2 0 0 0 2-2V6ZM8.75 7.75a.75.75 0 0 0-1.5 0v2.69L6.03 9.22a.75.75 0 0 0-1.06 1.06l2.5 2.5a.75.75 0 0 0 1.06 0l2.5-2.5a.75.75 0 1 0-1.06-1.06l-1.22 1.22V7.75Z"
                    clip-rule="evenodd"
                />
            </svg>
        </div>
        <div class=" self-center text-sm font-medium">
            {$i18n.t('Download Performance Metric')}
        </div>
    </button>

    <button
        type="button"
        class=" flex rounded-md py-2 px-3 w-full hover:bg-gray-200 dark:hover:bg-gray-800 transition"
        on:click={async () => {
            document.getElementById('config-json-input').click();
        }}
    >
        <div class=" self-center mr-3">
            <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 16 16"
                fill="currentColor"
                class="w-4 h-4"
            >
                <path d="M2 3a1 1 0 0 1 1-1h10a1 1 0 0 1 1 1v1a1 1 0 0 1-1 1H3a1 1 0 0 1-1-1V3Z" />
                <path
                    fill-rule="evenodd"
                    d="M13 6H3v6a2 2 0 0 0 2 2h6a2 2 0 0 0 2-2V6ZM8.75 7.75a.75.75 0 0 0-1.5 0v2.69L6.03 9.22a.75.75 0 0 0-1.06 1.06l2.5 2.5a.75.75 0 0 0 1.06 0l2.5-2.5a.75.75 0 1 0-1.06-1.06l-1.22 1.22V7.75Z"
                    clip-rule="evenodd"
                />
            </svg>
        </div>
        <div class=" self-center text-sm font-medium">
            {$i18n.t('Download Alert History')}
        </div>
    </button>
</div>




</div>
