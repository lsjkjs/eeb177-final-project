    library(ggplot2)
    Aves <- read.csv("output_Aves.csv", header = F, as.is = T)
    names(Aves) <- c("genus", "species", "minage", "maxage")
    head(Aves)

    ##         genus             species   minage  maxage
    ## 1  Martinavis    Martinavis minor 68.30000 68.3000
    ## 2   Eremochen  Eremochen russelli 11.95000 14.1815
    ## 3 Primocolius   Primocolius sigei 39.65000 39.6500
    ## 4   Miohierax    Miohierax stocki 25.61500 25.6150
    ## 5        Grus      Grus americana  0.06885  4.4665
    ## 6     Tshulia     Tshulia litorea 57.25000 57.2500

    Aves_occ <- ggplot(Aves, aes( species, ymin = maxage, ymax=minage, colour = genus))
    Aves_occ <- Aves_occ + geom_linerange()
    Aves_occ <- Aves_occ + theme(legend.position="none")
    Aves_occ <- Aves_occ + coord_flip()
    Aves_occ <- Aves_occ + labs(title = "Aves Fossil Occurrences", x = "Species", y = "Ma ago") + theme(plot.title = element_text(hjust = 0.5, size=22, face = "bold"), axis.title =element_text(size=20))
    Aves_occ <- Aves_occ + theme(axis.text.y = element_text(size=3), axis.ticks.y=element_blank())
    Aves_occ #contains whole data

![](plot_Aves_files/figure-markdown_strict/unnamed-chunk-1-1.png)

    ggsave("Aves_species_ranges.png", plot = Aves_occ)

    ## Saving 7 x 5 in image
