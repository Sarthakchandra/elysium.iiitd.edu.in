<script>
  import sponsors from '../../../data/sponsors.yml'

  import Section from '../section.svelte'
  import LinkIcon from '../icons/link.svelte'
  import Image from '../image.svelte'
</script>

<Section id={'sponsors'} heading={'Sponsors'} >
  <div class="gallery">
    {#each sponsors as sponsor}
      <a href='{sponsor.link}' target='_blank' rel='noopener'>
        <div class="image-wrapper">
          <Image src={sponsor.image} alt="{sponsor.name} logo" />
        </div>
        <span>
          {sponsor.name}
          <LinkIcon strokeColor="#eeeeee"/>
        </span>
      </a>
    {/each}
  </div>
</Section>

<style lang="scss">
  .gallery {
    display: flex;
    flex-wrap: wrap;
    margin: 2vh -4vh;

    a {
      margin: 4vh;
      flex: 1;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      font-size: 1.1rem;
      color: #eeeeee;
      text-decoration: none;
      font-weight: 400;
      transition: 0.1s opacity ease-in-out;
      opacity: 0.5;

      &:hover,
      &:focus,
      &:active {
        opacity: 1;

        :global(img) {
          filter: saturate(100%);
          transform: scale(1.1);
        }
      }

      span {
        display: flex;
        align-items: center;
        text-align: center;
        line-height: 1.5;
      }
    }

    .image-wrapper {
      flex: 1;
      display: flex;
      align-items: center;
      margin-bottom: 20px;

      :global(img) {
        max-height: #{'min(7.5vmax, 75px)'};
        max-width: 15vmax;
        align-self: center;
        transition: 0.1s all ease-in-out;
        filter: saturate(0%) brightness(2);

        @media only screen and (max-width: 800px) {
          filter: saturate(75%);
        }
      }
    }
  }
</style>
