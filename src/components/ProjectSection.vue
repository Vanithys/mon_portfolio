<template>
    <section class="final-section">
        <img class="final-image" src="@/assets/np.jpg" alt="Image qui représente une plage ensoleillée, avec des palmiers, une ville en arrière-plan, un avion et le texte 'New Paradise'.">
        <h2 class="final-title">PROJET - NEW PARADISE</h2>
        <p class="final-description">
            Un serveur FiveM en développement depuis un an, basé sur le framework QB-Core. Nous avons créé un environnement de jeu immersif et captivant qui redéfinit l’expérience à Los Santos. 
            Notre carte a été soigneusement retravaillée pour intégrer une végétation luxuriante et des paysages variés, offrant aux joueurs l'occasion d'explorer des zones inédites et d'apprécier la beauté naturelle de la ville. 
            Grâce à une sélection de scripts innovants et intuitifs, vous pourrez interagir avec le monde de manière fluide et engageante, que vous souhaitiez vous adonner à des activités légales ou plonger dans le monde du crime. 
            Nous mettons également un point d’honneur à favoriser une communauté active et conviviale, où chaque joueur peut s’épanouir et partager ses expériences. 
            Des événements réguliers et des compétitions passionnantes seront organisés pour garantir une expérience de jeu toujours renouvelée et dynamique. 
            Lorsque le projet sera terminé, nous vous invitons à nous rejoindre et à découvrir un nouveau chapitre de votre aventure à Los Santos, où chaque jour est une nouvelle opportunité d'explorer, d'apprendre et de vous divertir.
        </p>
    </section>
</template>

<script>
export default {
    name: 'ProjectSection',
};
</script>

<style>
.final-section {
    text-align: center;
    margin: 40px 0;
    padding: 30px;
    border-radius: 10px;
}

.final-image {
    max-width: 90%;
    height: auto;
    border-radius: 10px;
}

.final-title {
    font-size: 3em;
    color: #adfaff;
    margin: 20px 0;
}

.final-description {
    font-size: 1.3em;
    color: #d3d3d3;
    margin: 0 20px;
}
</style>