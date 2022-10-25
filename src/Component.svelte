<script>
  import { getContext } from "svelte";
  import { Card, CardBody, Row, Col } from "sveltestrap";

  export let tittle = "Tittle";
  export let value = "Value";
  export let subtittle = "Subtittle";
  export let icon = "ri-line-chart-fill";
  export let backgroundColor = "#f5365c";
  export let iconColor = "white";
  export let iconSize = 25;
  export let secondaryValue;
  export let compareSecondaryValueTo = "0";
  export let secondaryValueSuffix = "%";
  export let showIconColorComparison = true;
  export let aboveThreshholdIcon = "ri-arrow-up-fill";
  export let belowThreshholdIcon = "ri-arrow-down-fill";
  export let aboveThreshholdColor = "#2dce89";
  export let belowThreshholdColor = "#f5365c";

  const { styleable } = getContext("sdk");
  const component = getContext("component");
</script>

<svelte:head>
  <link
    rel="stylesheet"
    href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css"
  />
</svelte:head>

<Card style="min-width: 15rem; width: 100%;">
  <CardBody>
    <Row>
      <Col>
        <h5 class="card-title text-uppercase text-muted mb-0">{tittle}</h5>
        <span class="h2 font-weight-bold mb-0">{value}</span>
      </Col>
      <Col xs="auto">
        <div
          class="icon icon-shape rounded-circle {backgroundColor ? "shadow" : ""}"
          style="background-color:{backgroundColor};"
        >
          <i class={icon} style="color:{iconColor}; font-size:{iconSize}px" />
        </div>
      </Col>

      {#if secondaryValue || subtittle}
        <p class="mt-3 mb-0 text-muted text-sm">
          {#if secondaryValue}
            {#if showIconColorComparison}
              {#if parseFloat(secondaryValue) > parseFloat(compareSecondaryValueTo)}
                <i
                  class="{aboveThreshholdIcon} mr-1"
                  style="color: {aboveThreshholdColor};"
                /><span
                  class="text-nowrap mr-1"
                  style="color: {aboveThreshholdColor};"
                  >{secondaryValue}{secondaryValueSuffix}</span
                >
              {:else if parseFloat(secondaryValue) < parseFloat(compareSecondaryValueTo)}
                <i
                  class="{belowThreshholdIcon} mr-1 "
                  style="color: {belowThreshholdColor};"
                /><span
                  class="text-nowrap mr-1"
                  style="color: {belowThreshholdColor};"
                  >{secondaryValue}{secondaryValueSuffix}</span
                >
              {:else}
                <i class="ri-creative-commons-nd-fill mr-1" />
              {/if}
            {:else}
              <span class="text-nowrap mr-1">{secondaryValue}{secondaryValueSuffix}</span>
            {/if}
          {/if}
          {#if subtittle}
            <span class="text-nowrap">{subtittle}</span>
          {/if}
        </p>
      {/if}
    </Row>
  </CardBody>
</Card>

<style>
  h5 {
    margin-top: 0;
    margin-bottom: 0.5rem;
  }

  p {
    margin-top: 0;
    margin-bottom: 1rem;
  }

  h5,
  .h2,
  .h5 {
    font-family: inherit;
    font-weight: 600;
    line-height: 1.5;
    margin-bottom: 0.5rem;
    color: #32325d;
  }

  .h2 {
    font-size: 1.25rem;
  }

  h5,
  .h5 {
    font-size: 0.8125rem;
  }

  .shadow {
    box-shadow: 0 0 2rem 0 rgba(136, 152, 170, 0.15) !important;
  }

  .mb-0 {
    margin-bottom: 0 !important;
  }

  .mr-2 {
    margin-right: 0.5rem !important;
  }

  .mr-1 {
    margin-right: 0.25rem !important;
  }

  .ml-2 {
    margin-left: 0.5rem !important;
  }

  .mt-3 {
    margin-top: 1rem !important;
  }

  .mb-4 {
    margin-bottom: 1.5rem !important;
  }

  .mb-5 {
    margin-bottom: 3rem !important;
  }

  .pt-5 {
    padding-top: 3rem !important;
  }

  .pb-8 {
    padding-bottom: 8rem !important;
  }

  .text-nowrap {
    white-space: nowrap !important;
  }

  .text-center {
    text-align: center !important;
  }

  .text-uppercase {
    text-transform: uppercase !important;
  }

  .font-weight-bold {
    font-weight: 600 !important;
  }

  .text-muted {
    color: #8898aa !important;
  }

  .text-red {
    color: #f5365c !important;
  }

  .text-green {
    color: #2dce89 !important;
  }

  .text-sm {
    font-size: 0.875rem !important;
    display: flex;
    vertical-align: center;
  }

  .icon {
    width: 3rem;
    height: 3rem;
  }

  .icon-shape {
    display: inline-flex;
    padding: 12px;
    text-align: center;
    border-radius: 50%;
    align-items: center;
    justify-content: center;
  }

  p {
    font-size: 1rem;
    font-weight: 300;
    line-height: 1.7;
  }
</style>
