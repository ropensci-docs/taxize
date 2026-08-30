# Get a random vector of species names.

Family and order names come from the APG plant names list. Genus and
species names come from Theplantlist.org.

## Usage

``` r
names_list(rank = "genus", size = 10)
```

## Arguments

- rank:

  (character) Taxonomic rank, one of species, genus (default), family,
  order

- size:

  (integer/numeric) Number of names to get. Maximum depends on the rank

## Value

character vector of taxonomic names

## Author

Scott Chamberlain

## Examples

``` r
names_list()
#>  [1] "Sinclairia"      "Dryopteris"      "Mirabilis"       "Macrolejeunea"  
#>  [5] "Scilla"          "Austrosteenisia" "Corybas"         "Glyphochloa"    
#>  [9] "Comarostaphylis" "Platycaulos"    
names_list('species')
#>  [1] "Calea lucidivenia"      "Salvia miltiorrhiza"    "Kaempferia grandifolia"
#>  [4] "Columnea inaequilatera" "Citrus truncata"        "Hieracium vindobonense"
#>  [7] "Carex typhina"          "Allocasuarina fibrosa"  "Cistus eulaliae"       
#> [10] "Bulbostylis burchellii"
names_list('genus')
#>  [1] "Acicarpha"     "Ponerorchis"   "Ampelocissus"  "Vernoniastrum"
#>  [5] "Nopalea"       "Markea"        "Clitoria"      "Brachistus"   
#>  [9] "Madagaster"    "Amphiblemma"  
names_list('family')
#>  [1] "Asphodelaceae"  "Lamiaceae"      "Amaranthaceae"  "Sarcolaenaceae"
#>  [5] "Thymelaeaceae"  "Cupressaceae"   "Winteraceae"    "Burseraceae"   
#>  [9] "Peraceae"       "Apiaceae"      
names_list('order')
#>  [1] "Nymphaeales"    "Cycadales"      "Brassicales"    "Lamiales"      
#>  [5] "Caryophyllales" "Poales"         "Malpighiales"   "Lamiales"      
#>  [9] "Chloranthales"  "Brassicales"   
names_list('order', 2)
#> [1] "Ericales"  "Asterales"
names_list('order', 15)
#>  [1] "Oxalidales"       "Rosales"          "Caryophyllales"   "Alismatales"     
#>  [5] "Alismatales"      "Asterales"        "Solanales"        "Cornales"        
#>  [9] "Austrobaileyales" "Caryophyllales"   "Brassicales"      "Salviniales."    
#> [13] "Lycopodiales"     "Malpighiales"     "Caryophyllales"  

# You can get a lot of genus or species names if you want
nrow(theplantlist)
#> [1] 10000
names_list('genus', 500)
#>   [1] "Cinnadenia"         "Cornus"             "Stachytarpheta"    
#>   [4] "Lachenalia"         "Catachaetum"        "Notothylas"        
#>   [7] "Kickxia"            "Hydnophytum"        "Suberanthus"       
#>  [10] "Chresta"            "Cissus"             "Aristida"          
#>  [13] "Sterculia"          "Struthiopteris"     "Radiovittaria"     
#>  [16] "Polypodium"         "Lawrencia"          "Calytrix"          
#>  [19] "Philammos"          "Garovaglia"         "Racosperma"        
#>  [22] "Calamus"            "Gypsophila"         "Lescuraea"         
#>  [25] "Guanchezia"         "Crudia"             "Tricholepis"       
#>  [28] "Trichosanthes"      "Epipremnum"         "Pancratium"        
#>  [31] "Ixia"               "Acetosella"         "Blakea"            
#>  [34] "Lodoicea"           "Endiandra"          "Vernasolis"        
#>  [37] "Actinocephalus"     "Macaranga"          "Perovskia"         
#>  [40] "Scaphyglottis"      "Grewia"             "Sarcosperma"       
#>  [43] "Amphidasya"         "Upopion"            "Rhaphidophora"     
#>  [46] "Staurogyne"         "Rungia"             "Corydalis"         
#>  [49] "Loasa"              "Fraxinus"           "Lachemilla"        
#>  [52] "Anoectochilus"      "Leucopogon"         "Pilotrichum"       
#>  [55] "Centaurea"          "Gastrochilus"       "Adenosma"          
#>  [58] "Lellingeria"        "Aptandra"           "Filago"            
#>  [61] "Erysimum"           "Acrostichum"        "Euonymus"          
#>  [64] "Gutenbergia"        "Nepenthes"          "Phaseolus"         
#>  [67] "Cayratia"           "Echinospermum"      "Hypertelis"        
#>  [70] "Thlaspi"            "Alysicarpus"        "Drepanolejeunea"   
#>  [73] "Zehneria"           "Stenia"             "Philadelphus"      
#>  [76] "Orthaea"            "Calanthe"           "Ornithogalum"      
#>  [79] "Piptadenia"         "Boerhavia"          "Hemigraphis"       
#>  [82] "Oryza"              "Pseudosclerochloa"  "Mentha"            
#>  [85] "Capsella"           "Sebastiania"        "Microtropis"       
#>  [88] "Aureolaria"         "Hedyosmum"          "Spilanthes"        
#>  [91] "Parkia"             "Cadetia"            "Ceratolejeunea"    
#>  [94] "Miricacalia"        "Taeniophyllum"      "Stachys"           
#>  [97] "Pariana"            "Elettariopsis"      "Barbaceniopsis"    
#> [100] "Renealmia"          "Puccinellia"        "Illicium"          
#> [103] "Pleroma"            "Virgilia"           "Pennisetum"        
#> [106] "Pontia"             "Schoenorchis"       "Odontolophus"      
#> [109] "Conandrium"         "Ophiocaulon"        "Ticorea"           
#> [112] "Dressleria"         "Schismatoglottis"   "Hylomecon"         
#> [115] "Multidentia"        "Tournefortia"       "Alectra"           
#> [118] "Brasilidium"        "Crossopetalum"      "Doliocarpus"       
#> [121] "Phanerophlebiopsis" "Primulidium"        "Ziziphus"          
#> [124] "Acourtia"           "Jacksonia"          "Mayna"             
#> [127] "Stenandrium"        "Cuviera"            "Handroanthus"      
#> [130] "Leucodon"           "Polygala"           "Lycopodium"        
#> [133] "Oxycarpus"          "Loxogramme"         "Rollinia"          
#> [136] "Leptotheca"         "Romanzoffia"        "Phacelia"          
#> [139] "Piptomeris"         "Weigela"            "Haemodorum"        
#> [142] "Eucrosia"           "Eriodictyon"        "Tristemon"         
#> [145] "Laguncularia"       "Wendlandia"         "Ligularia"         
#> [148] "Phaseolodes"        "Macrolejeunea"      "Cupaniopsis"       
#> [151] "Eschweilera"        "Coryphantha"        "Belmontia"         
#> [154] "Papaver"            "Xeroderris"         "Oxymeris"          
#> [157] "Chamaedorea"        "Spiesia"            "Arabis"            
#> [160] "Millettia"          "Mosenodendron"      "Sagittaria"        
#> [163] "Atylosia"           "Ophrys"             "Leptinella"        
#> [166] "Myrsine"            "Distasis"           "Mauria"            
#> [169] "Phyllocactus"       "Gomphia"            "Coreopsis"         
#> [172] "Paphiopedilum"      "Botrypus"           "Antimima"          
#> [175] "Spartium"           "Flourensia"         "Horsfieldia"       
#> [178] "Syntrichia"         "Guadua"             "Agelanthus"        
#> [181] "Oxylobium"          "Brachionidium"      "Prasophyllum"      
#> [184] "Anthyllis"          "Phyllagathis"       "Maytenus"          
#> [187] "Teucrium"           "Centella"           "Vittaria"          
#> [190] "Pelexia"            "Pilotrichella"      "Helictochloa"      
#> [193] "Vitex"              "Jacea"              "Bunium"            
#> [196] "Neomirandea"        "Cremanthodium"      "Psammophiliella"   
#> [199] "Ampelosicyos"       "Bruchia"            "Padus"             
#> [202] "Parashorea"         "Urostachys"         "Diaphananthe"      
#> [205] "Seseli"             "Erpodium"           "Brachiolejeunea"   
#> [208] "Santaloides"        "Otholobium"         "Bossiaea"          
#> [211] "Lysinema"           "Astartea"           "Rodgersia"         
#> [214] "Pergularia"         "Coniogramme"        "Octoblepharum"     
#> [217] "Phylica"            "Heterostemma"       "Fagara"            
#> [220] "Roupala"            "Rodriguezia"        "Dichelyma"         
#> [223] "Jasminum"           "Carpotroche"        "Najas"             
#> [226] "Centinodia"         "Dioscoreophyllum"   "Dendropemon"       
#> [229] "Zaluzianskya"       "Quesnelia"          "Benthamia"         
#> [232] "Thomasia"           "Mesembryanthemum"   "Lizeron"           
#> [235] "Narcissus"          "Cleistanthus"       "Galeandra"         
#> [238] "Helenium"           "Gratiola"           "Aptosimum"         
#> [241] "Blechum"            "Melanophylla"       "Impatiens"         
#> [244] "Rafnia"             "Montrichardia"      "Tetrorchidium"     
#> [247] "Libanotis"          "Ptelea"             "Tragacantha"       
#> [250] "Arachniodes"        "Elleanthus"         "Camassia"          
#> [253] "Psephellus"         "Robinia"            "Dais"              
#> [256] "Quincula"           "Microcampylopus"    "Verbena"           
#> [259] "Elatostema"         "Gossypium"          "Brunellia"         
#> [262] "Pseudognaphalium"   "Onobrychis"         "Ledebouria"        
#> [265] "Cosmibuena"         "Pylaisia"           "Tachigali"         
#> [268] "Mammillaria"        "Caldesia"           "Clusia"            
#> [271] "Poranopsis"         "Epithema"           "Asclepias"         
#> [274] "Omphalospora"       "Lagerstroemia"      "Cristaria"         
#> [277] "Astilbe"            "Cryptadenia"        "Philonotion"       
#> [280] "Tetragonotheca"     "Zephyranthes"       "Eleiotis"          
#> [283] "Ehretia"            "Sabatia"            "Paraspalathus"     
#> [286] "Staphidium"         "Spinifex"           "Tamarix"           
#> [289] "Sinapis"            "Berkheya"           "Mirabilis"         
#> [292] "Gelonium"           "Gackstroemia"       "Sonerila"          
#> [295] "Jacobaea"           "Arenaria"           "Endotrichum"       
#> [298] "Agalmyla"           "Bakeridesia"        "Piper"             
#> [301] "Lavenia"            "Schizomitrium"      "Allocarya"         
#> [304] "Lepidium"           "Arum"               "Frullania"         
#> [307] "Ebnerella"          "Escobaria"          "Rhoicissus"        
#> [310] "Anisopappus"        "Heuchera"           "Globba"            
#> [313] "Hygrolejeunea"      "Rhipsalis"          "Ceratostema"       
#> [316] "Syzygiella"         "Dolichostachys"     "Grias"             
#> [319] "Pyxidaria"          "Rebutia"            "Plagiothecium"     
#> [322] "Calymperes"         "Bryonia"            "Dipteracanthus"    
#> [325] "Cystea"             "Sericocalyx"        "Andinia"           
#> [328] "Pentameris"         "Spathiphyllum"      "Plesioneuron"      
#> [331] "Podalyria"          "Stissera"           "Oldenlandia"       
#> [334] "Gynandropsis"       "Chilita"            "Linosyris"         
#> [337] "Acmella"            "Cyrtomium"          "Pterygodium"       
#> [340] "Polybotrya"         "Lithops"            "Chelonistele"      
#> [343] "Sindora"            "Weingartia"         "Leymus"            
#> [346] "Tripleurothemis"    "Cyclophyllum"       "Heteromma"         
#> [349] "Eminium"            "Cryptocarya"        "Anacolosa"         
#> [352] "Cynoglossum"        "Spermacoce"         "Connarus"          
#> [355] "Lactuca"            "Synsepalum"         "Hedyotis"          
#> [358] "Leutea"             "Hexalobus"          "Notelaea"          
#> [361] "Erica"              "Anila"              "Thereianthus"      
#> [364] "Manulea"            "Tovomita"           "Sonchus"           
#> [367] "Cynophalla"         "Mycaranthes"        "Celosia"           
#> [370] "Hypochaeris"        "Psiadia"            "Kuhlhasseltia"     
#> [373] "Psittacanthus"      "Schoenocaulon"      "Polystachya"       
#> [376] "Cynontodium"        "Tuzibeanthus"       "Sebaea"            
#> [379] "Condylopodium"      "Actinophlebia"      "Tellima"           
#> [382] "Saxifraga"          "Axonopus"           "Pleurogramme"      
#> [385] "Orophea"            "Villaresia"         "Taxilejeunea"      
#> [388] "Muricococcum"       "Rumex"              "Topobea"           
#> [391] "Neoporteria"        "Pedersenia"         "Acuan"             
#> [394] "Athrixia"           "Hymenolyma"         "Polygonum"         
#> [397] "Sarracenia"         "Breweriopsis"       "Capsicum"          
#> [400] "Breidleria"         "Petrocosmea"        "Bretschneidera"    
#> [403] "Gnaphalium"         "Scalesia"           "Cystopteris"       
#> [406] "Vicia"              "Mollia"             "Alansmia"          
#> [409] "Quercus"            "Abronia"            "Crenias"           
#> [412] "Photinia"           "Porothamnium"       "Nonea"             
#> [415] "Calyptranthes"      "Moringa"            "Tridophyllum"      
#> [418] "Sideroxylon"        "Struthiola"         "Calendula"         
#> [421] "Hedychium"          "Macroptilium"       "Sarmentypnum"      
#> [424] "Citronella"         "Idiothamnus"        "Hackelia"          
#> [427] "Sinochasea"         "Pseudolmedia"       "Elymotrigia"       
#> [430] "Niedenzuella"       "Androsace"          "Pityrodia"         
#> [433] "Tagetes"            "Muraltia"           "Stereodon"         
#> [436] "Pleuridium"         "Claopodium"         "Klenzea"           
#> [439] "Rhododendron"       "Archilejeunea"      "Eriosyce"          
#> [442] "Crossomitrium"      "Dactylorhiza"       "Barclaya"          
#> [445] "Fragaria"           "Linum"              "Aptychella"        
#> [448] "Huilaea"            "Kaempferia"         "Calandrinia"       
#> [451] "Silaus"             "Myrrhidium"         "Rafflesia"         
#> [454] "Lavatera"           "Microchilus"        "Gymnobalanus"      
#> [457] "Cacalia"            "Mikania"            "Elmera"            
#> [460] "Micropiper"         "Chrysosplenium"     "Juniperus"         
#> [463] "Tradescantia"       "Thesium"            "Ostrya"            
#> [466] "Gymnogramma"        "Menonvillea"        "Codonopsis"        
#> [469] "Rhacopilopsis"      "Palicourea"         "Kunzea"            
#> [472] "Panicum"            "Dicraeia"           "Yucca"             
#> [475] "Scutellaria"        "Peraxilla"          "Chaunanthus"       
#> [478] "Antidesma"          "Lithocarpus"        "Hemizonia"         
#> [481] "Ageratina"          "Marcgravia"         "Orchis"            
#> [484] "Aphanorrhegma"      "Glyceria"           "Calypogeia"        
#> [487] "Decaspermum"        "Eulalia"            "Ephedra"           
#> [490] "Woodvillea"         "Mosannona"          "Orthion"           
#> [493] "Bergenia"           "Helianthocereus"    "Pittosporum"       
#> [496] "Gymnosiphon"        "Utricularia"        "Coreocarpus"       
#> [499] "Hebe"               "Urophyllum"        
```
