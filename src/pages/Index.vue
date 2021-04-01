<template>
  <q-page>
    <div class="row">
      <div class="col"></div>
      <div class="col-8">
        <h2 class="text-center">Bienvenue sur Poster shop !</h2>
      </div>
      <div class="col"></div>
    </div>
    <div class="row">
      <div class="col-1"></div>
      <div class="col-4">
        <h4>Des posters pour chaque pièce</h4>
        <p>Nous vous proposons toute une gamme d’affiches, de cadres et de posters en ligne esthétiques et tendance pour chaque pièce. Vous cherchez des posters mignons pour la chambre de votre enfant? Ou des affiches tendance pour votre salon ? Nous avons tout cela sur Poster-shop.com. La satisfaction client est notre priorité, c’est pourquoi nous offrons toujours des prix bas et des livraisons rapides. L’achat de posters en ligne doit être simple et la livraison rapide.</p>
        <br/>
        <p>Nous nous passionnons pour les intérieurs, le design et les tendances. Nous savons qu’il est important de bien assortir un poster ou une affiche avec le design d’un intérieur, pour profiter de la beauté de son environnement. Pour trouver des idées ou de l’inspiration, n’hésitez pas à parcourir notre magazine, nos collections ainsi que nos diverses décorations murales. Votre achat de posters en ligne doit être plaisant et simple.</p>
        <br/>
        <p>Aménagez votre intérieur et laissez-vous inspirer par un large choix d’idées déco, d’accessoires et de décorations murales. Vous trouverez un très large choix dans notre boutique en ligne de : stickers muraux, tableaux, papiers peints, idées déco ou lettres décoratives 3D mais également des décorations pour vos fenêtres, portes ou carrelage. Il y en a pour tous les âges et pour tous les goûts.

Des marques exclusives et probablement la plus grande sélection de motifs pour enfants. Poster shop est l'une des plus grandes boutiques en ligne pour les stickers muraux en Europe et a été classée meilleure boutique de stickers 2013 par getested.de.</p>
        <p>Choisissez votre tableau préféré parmi nos tableaux ou poster et donnez un style à vos murs. Transformez votre intérieur avec notre collection de papier peint aux motifs modernes et adaptés à tous les styles ou optez pour le papier peint photo si vous êtes un amoureux des grands espaces, un passionné d’architecture ou un fan des lofts new yorkais. Vous trouverez certainement votre bonheur.</p>
      </div>
      <div class="col-2"></div>
      <div class="col-4">
        <h5 class="text-center">NOS FAVORIS DU MOMENT</h5>
        <div class="q-pa-md">
          <q-carousel
            animated
            v-model="slide"
            arrows
            navigation
            infinite
            autoplay="true"
          >
            <q-carousel-slide :name="1" img-src="~assets/images/poster-citron.jpg" />
            <q-carousel-slide :name="2" img-src="~assets/images/poster-lac.jpg" />
            <q-carousel-slide :name="3" img-src="~assets/images/poster-vase.jpg" />
            <q-carousel-slide :name="4" img-src="~assets/images/poster-planete.jpg" />
          </q-carousel>
        </div>
        <div class="row justify-center">
<q-btn outline color="primary" @click="$router.replace('/shop')" label="Découvrir le catalogue" icon="local_grocery_store" />
        </div>
      </div>
      <div class="col-1"></div>
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data () {
    return {
      slide: 1
    }
  }
}
</script>
