import { useState } from "react";

const GF = `@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400&family=Lato:wght@300;400;700&display=swap');`;

// varietals: [] = unknown/unconfirmed, leave blank rather than guess
const WINERIES = [
  // Aug 2025
  {id:1,permit:"00141-02",name:"Willamette Valley Vineyards",city:"Turner",state:"OR",approved:"2025-08-11",url:"https://www.wvv.com",local:false,v:["Pinot Noir","Pinot Gris","Chardonnay","Riesling"]},
  // Sep 2025
  {id:2,permit:"26305-01",name:"Biltmore Estate Wine Company",city:"Asheville",state:"NC",approved:"2025-09-10",url:"https://shop.biltmore.com/collections/wine",local:false,v:["Cabernet Sauvignon","Chardonnay","Sparkling","Pinot Grigio"]},
  {id:3,permit:"26306-01",name:"Sutter Home Winery",city:"St. Helena",state:"CA",approved:"2025-09-10",url:"https://www.sutterhome.com",local:false,v:["White Zinfandel","Cabernet Sauvignon","Moscato","Chardonnay"]},
  {id:4,permit:"26307-01",name:"Avaline",city:"Healdsburg",state:"CA",approved:"2025-09-10",url:"https://drinkavalina.com",local:false,v:["Chardonnay","Rosé","Red Blend"]},
  {id:5,permit:"26308-01",name:"Windsor Vineyards",city:"Kelseyville",state:"CA",approved:"2025-09-10",url:"https://www.windsorvineyards.com",local:false,v:["Cabernet Sauvignon","Chardonnay","Pinot Noir","Zinfandel"]},
  {id:6,permit:"26322-01",name:"Lionstone International",city:"Santa Rosa",state:"CA",approved:"2025-09-15",url:"https://www.lionstone.com",local:false,v:["Various (200+ Exclusives)"]},
  {id:7,permit:"26323-01",name:"Lionstone International",city:"Napa",state:"CA",approved:"2025-09-15",url:"https://www.lionstone.com",local:false,v:["Various (200+ Exclusives)"]},
  {id:8,permit:"26325-01",name:"Lionstone International",city:"Ukiah",state:"CA",approved:"2025-09-15",url:"https://www.lionstone.com",local:false,v:["Various (200+ Exclusives)"]},
  {id:9,permit:"26326-01",name:"Lionstone International",city:"Napa",state:"CA",approved:"2025-09-15",url:"https://www.lionstone.com",local:false,v:["Various (200+ Exclusives)"]},
  {id:10,permit:"26327-01",name:"Lionstone International",city:"St. Helena",state:"CA",approved:"2025-09-15",url:"https://www.lionstone.com",local:false,v:["Various (200+ Exclusives)"]},
  {id:11,permit:"26348-01",name:"Sherwin Family Vineyards",city:"St. Helena",state:"CA",approved:"2025-09-22",url:"https://www.sherwinfamilyvineyards.com",local:false,v:["Cabernet Sauvignon"]},
  {id:12,permit:"26349-01",name:"Switchback Ridge",city:"St. Helena",state:"CA",approved:"2025-09-22",url:"https://www.switchbackridge.com",local:false,v:["Cabernet Sauvignon","Merlot","Petite Sirah"]},
  {id:14,permit:"26351-01",name:"Gestalt Wine Company",city:"Napa",state:"CA",approved:"2025-09-22",url:"https://www.gestaltwinecompany.com",local:false,v:[]},
  {id:15,permit:"26352-01",name:"Mark Ryan Winery",city:"Walla Walla",state:"WA",approved:"2025-09-22",url:"https://www.markryanwinery.com",local:false,v:["Cabernet Sauvignon","Red Blends","Grenache"]},
  {id:16,permit:"26353-01",name:"Dawns Dream",city:"Gonzales",state:"CA",approved:"2025-09-22",url:"https://www.dawnsdreamwinery.com",local:false,v:[]},
  {id:17,permit:"26354-01",name:"Galante Winery",city:"Carmel Valley",state:"CA",approved:"2025-09-22",url:"https://www.galantewines.com",local:false,v:["Cabernet Sauvignon","Sauvignon Blanc","Rosé"]},
  {id:18,permit:"26356-01",name:"Republican Red",city:"Soledad",state:"CA",approved:"2025-09-22",url:"https://republicanred.com",local:false,v:[]},
  {id:19,permit:"26357-01",name:"Michael David Winery",city:"Lodi",state:"CA",approved:"2025-09-22",url:"https://www.michaeldavidwinery.com",local:false,v:["Zinfandel","Cabernet Sauvignon","Petite Sirah"]},
  {id:20,permit:"26358-01",name:"Flora Springs",city:"St. Helena",state:"CA",approved:"2025-09-22",url:"https://www.florasprings.com",local:false,v:["Cabernet Sauvignon","Chardonnay","Merlot","Sangiovese"]},
  {id:21,permit:"26359-01",name:"Laura Michael Wines",city:"Calistoga",state:"CA",approved:"2025-09-22",url:"https://lauramichaelwines.com",local:false,v:[]},
  {id:22,permit:"26408-01",name:"Williams Selyem",city:"Healdsburg",state:"CA",approved:"2025-09-29",url:"https://www.williamselyem.com",local:false,v:["Pinot Noir","Chardonnay","Zinfandel"]},
  {id:23,permit:"26410-01",name:"Leonetti Cellar",city:"Walla Walla",state:"WA",approved:"2025-09-29",url:"https://www.leonetticellar.com",local:false,v:["Cabernet Sauvignon","Merlot","Sangiovese"]},
  {id:24,permit:"26411-01",name:"Figgins Estate",city:"Walla Walla",state:"WA",approved:"2025-09-29",url:"https://www.figginsfamilywine.com",local:false,v:["Cabernet Sauvignon","Merlot","Syrah"]},
  {id:25,permit:"26413-01",name:"Bouchaine Vineyards",city:"Napa",state:"CA",approved:"2025-09-30",url:"https://www.bouchaine.com",local:false,v:["Pinot Noir","Chardonnay","Pinot Gris"]},
  {id:26,permit:"26414-01",name:"Pax Mahle Wines",city:"Sebastopol",state:"CA",approved:"2025-09-30",url:"https://www.paxwine.com",local:false,v:["Syrah","Grenache","Mourvèdre","Roussanne"]},
  {id:27,permit:"26416-01",name:"De Negoce",city:"Santa Rosa",state:"CA",approved:"2025-09-30",url:"https://www.denegoce.com",local:false,v:["Various (Négociant)"]},
  {id:28,permit:"26417-01",name:"Mitchell Katz Winery",city:"Livermore",state:"CA",approved:"2025-09-30",url:"https://www.mitchellkatzwinery.com",local:false,v:["Petite Sirah","Chardonnay","Cabernet Sauvignon"]},
  {id:29,permit:"26418-01",name:"Ehlers Estate",city:"St. Helena",state:"CA",approved:"2025-09-30",url:"https://www.ehlersestate.com",local:false,v:["Cabernet Sauvignon","Merlot","Sauvignon Blanc","Cab Franc"]},
  // Oct 2025
  {id:30,permit:"26437-01",name:"Bedrock Wine Co.",city:"Sonoma",state:"CA",approved:"2025-10-06",url:"https://www.bedrockwineco.com",local:false,v:["Zinfandel","Syrah","Old Vine Blends","Rosé"]},
  {id:31,permit:"26439-01",name:"F. Korbel & Bros.",city:"Guerneville",state:"CA",approved:"2025-10-06",url:"https://www.korbel.com",local:false,v:["Brut","Blanc de Blancs","Rosé","Sparkling"]},
  {id:32,permit:"26460-01",name:"Medly Wine Co.",city:"Stonewall",state:"TX",approved:"2025-10-13",url:"https://www.drinkmedly.com",local:false,v:[]},
  {id:34,permit:"26463-01",name:"Raptor Ridge Winery",city:"Newberg",state:"OR",approved:"2025-10-13",url:"https://www.raptorridgewinery.com",local:false,v:["Pinot Noir","Pinot Gris","Rosé"]},
  {id:35,permit:"26465-01",name:"Walla Walla Vintners",city:"Walla Walla",state:"WA",approved:"2025-10-13",url:"https://www.wallawallavintners.com",local:false,v:["Cabernet Sauvignon","Merlot","Syrah","Sangiovese"]},
  {id:37,permit:"26468-01",name:"Lincourt Vineyards",city:"Solvang",state:"CA",approved:"2025-10-13",url:"https://www.lincourtvineyard.com",local:false,v:["Chardonnay","Pinot Noir","Syrah","Cab Franc"]},
  {id:38,permit:"26525-01",name:"Hawks Hill Ranch Winery",city:"Paso Robles",state:"CA",approved:"2025-10-28",url:"https://www.hhrwinery.com",local:false,v:["Syrah","Grenache","Mourvèdre"]},
  {id:39,permit:"26526-01",name:"Summerwood Winery & Inn",city:"Paso Robles",state:"CA",approved:"2025-10-28",url:"https://www.summerwoodwinery.com",local:false,v:["Cabernet Sauvignon","Rhône Blends","Chardonnay"]},
  {id:40,permit:"26527-01",name:"The Mascot",city:"Oakville",state:"CA",approved:"2025-10-28",url:"https://www.mascotwine.com",local:false,v:["Cabernet Sauvignon"]},
  {id:41,permit:"26528-01",name:"White Rose Estate",city:"Dayton",state:"OR",approved:"2025-10-28",url:"https://www.whiterosestatewinery.com",local:false,v:["Pinot Noir","Pinot Gris","Rosé"]},
  {id:42,permit:"26529-01",name:"Bjornson Vineyard",city:"Salem",state:"OR",approved:"2025-10-28",url:"https://www.bjornsonwine.com",local:false,v:["Pinot Noir","Chardonnay","Pinot Gris"]},
  {id:43,permit:"26531-01",name:"Frichette Winery",city:"Benton City",state:"WA",approved:"2025-10-28",url:"https://www.frichettewinery.com",local:false,v:["Cabernet Sauvignon","Bordeaux Blends"]},
  {id:44,permit:"26532-01",name:"Martinelli Winery",city:"Windsor",state:"CA",approved:"2025-10-28",url:"https://www.martinelliwinery.com",local:false,v:["Zinfandel","Pinot Noir","Chardonnay"]},
  {id:45,permit:"26533-01",name:"Winston Winery",city:"Healdsburg",state:"CA",approved:"2025-10-28",url:"https://jwinstonwinery.com",local:false,v:[]},
  {id:46,permit:"26534-01",name:"Rudd Winery",city:"Oakville",state:"CA",approved:"2025-10-28",url:"https://www.ruddwinery.com",local:false,v:["Cabernet Sauvignon","Sauvignon Blanc"]},
  {id:47,permit:"26535-01",name:"Brooks Wines",city:"Amity",state:"OR",approved:"2025-10-28",url:"https://www.brookswines.com",local:false,v:["Pinot Noir","Riesling","Rosé"]},
  {id:48,permit:"26536-01",name:"Bennett Lane Winery",city:"Calistoga",state:"CA",approved:"2025-10-28",url:"https://www.bennettlanewinery.com",local:false,v:["Cabernet Sauvignon","MAXIMUS Red Blend"]},
  {id:49,permit:"26537-01",name:"Peter Michael Winery",city:"Calistoga",state:"CA",approved:"2025-10-28",url:"https://www.petermichaelwinery.com",local:false,v:["Chardonnay","Pinot Noir","Cabernet Sauvignon"]},
  {id:50,permit:"26538-01",name:"Cedar Hill Collective",city:"Healdsburg",state:"CA",approved:"2025-10-28",url:null,local:false,v:[]},
  {id:51,permit:"26539-01",name:"Turtle Rock Vineyards",city:"Paso Robles",state:"CA",approved:"2025-10-28",url:"https://www.turtlerockvineyards.com",local:false,v:[]},
  {id:52,permit:"26541-01",name:"Overshine Wine Co.",city:"Healdsburg",state:"CA",approved:"2025-10-28",url:"https://www.overshinewines.com",local:false,v:[]},
  {id:53,permit:"26542-01",name:"Jackson Hole Winery",city:"Jackson",state:"WY",approved:"2025-10-28",url:"https://www.jacksonholewinery.com",local:false,v:["Cabernet Sauvignon","Chardonnay","Riesling"]},
  // Nov 2025
  {id:54,permit:"26564-01",name:"Brown Estate Vineyards",city:"St. Helena",state:"CA",approved:"2025-11-03",url:"https://www.brownestate.com",local:false,v:["Zinfandel","Cabernet Sauvignon","Chardonnay"]},
  {id:55,permit:"26568-01",name:"MacRostie Winery",city:"Healdsburg",state:"CA",approved:"2025-11-03",url:"https://www.macrostiewinery.com",local:false,v:["Chardonnay","Pinot Noir"]},
  {id:56,permit:"26569-01",name:"Markham Vineyards",city:"St. Helena",state:"CA",approved:"2025-11-03",url:"https://www.markhamvineyards.com",local:false,v:["Cabernet Sauvignon","Merlot","Chardonnay","Sauvignon Blanc"]},
  {id:57,permit:"26570-01",name:"Argyle Winery",city:"Dundee",state:"OR",approved:"2025-11-03",url:"https://www.argylewinery.com",local:false,v:["Pinot Noir","Chardonnay","Sparkling","Riesling"]},
  {id:58,permit:"26572-01",name:"Knights Bridge Winery",city:"Calistoga",state:"CA",approved:"2025-11-03",url:"https://www.knightsbridgewinery.com",local:false,v:["Cabernet Sauvignon","Sauvignon Blanc"]},
  {id:59,permit:"26581-01",name:"The Walls",city:"Walla Walla",state:"WA",approved:"2025-11-10",url:"https://www.thewallswinery.com",local:false,v:["Syrah","Grenache","Chardonnay"]},
  {id:60,permit:"26582-01",name:"Chateau Diana",city:"Healdsburg",state:"CA",approved:"2025-11-10",url:"https://www.chateaudiana.com",local:false,v:["Cabernet Sauvignon","Chardonnay","Merlot"]},
  {id:61,permit:"26583-01",name:"Amulet Estate",city:"St. Helena",state:"CA",approved:"2025-11-10",url:"https://www.amuletestate.com",local:false,v:["Cabernet Sauvignon","Chardonnay"]},
  {id:62,permit:"26584-01",name:"Tusk Estates",city:"Napa",state:"CA",approved:"2025-11-10",url:"https://www.tuskestates.com",local:false,v:["Cabernet Sauvignon","L'Orange Red Blend"]},
  {id:63,permit:"26585-01",name:"Ladera Winery",city:"Calistoga",state:"CA",approved:"2025-11-10",url:"https://www.laderawinery.com",local:false,v:["Cabernet Sauvignon"]},
  {id:64,permit:"26586-01",name:"Signorello Estate",city:"Napa",state:"CA",approved:"2025-11-10",url:"https://www.signorelloestate.com",local:false,v:["Cabernet Sauvignon","Chardonnay","Rosé"]},
  {id:65,permit:"26587-01",name:"Clos Solène",city:"Paso Robles",state:"CA",approved:"2025-11-10",url:"https://www.clossolene.com",local:false,v:["Grenache","Syrah","Mourvèdre","Roussanne"]},
  {id:66,permit:"26588-01",name:"Benom Wines",city:"Paso Robles",state:"CA",approved:"2025-11-10",url:"https://www.benomwines.com",local:false,v:["Cabernet Sauvignon","Rhône Blends"]},
  {id:67,permit:"26589-01",name:"Girls Gone Wine",city:"Broken Bow",state:"OK",approved:"2025-11-10",url:"https://www.thegirlsgonewine.com",local:false,v:[]},
  {id:68,permit:"26598-01",name:"Robert Foley Vineyards",city:"Angwin",state:"CA",approved:"2025-11-17",url:"https://www.robertfoleyvineyards.com",local:false,v:["Cabernet Sauvignon","Chardonnay","Merlot","Claret"]},
  {id:69,permit:"26599-01",name:"Kachina Cellars",city:"Napa",state:"CA",approved:"2025-11-17",url:null,local:false,v:[]},
  {id:70,permit:"26600-01",name:"Kachina Cellars",city:"Napa",state:"CA",approved:"2025-11-17",url:null,local:false,v:[]},
  {id:71,permit:"26601-01",name:"Baltic Porter Works",city:"Dundee",state:"OR",approved:"2025-11-17",url:null,local:false,v:[]},
  {id:72,permit:"26602-01",name:"Cider Works",city:"Lodi",state:"CA",approved:"2025-11-17",url:null,local:false,v:[]},
  {id:73,permit:"26603-01",name:"Altbier Operations",city:"Healdsburg",state:"CA",approved:"2025-11-17",url:null,local:false,v:[]},
  {id:74,permit:"26604-01",name:"Realm Cellars",city:"Napa",state:"CA",approved:"2025-11-17",url:"https://www.realmcellars.com",local:false,v:["Cabernet Sauvignon","Chardonnay","Proprietary Blends"]},
  // Dec 2025
  {id:75,permit:"26651-01",name:"Grassini Family Vineyards",city:"Santa Ynez",state:"CA",approved:"2025-12-01",url:"https://www.grassinifamilyvineyards.com",local:false,v:["Sauvignon Blanc","Cabernet Sauvignon","Syrah"]},
  {id:76,permit:"26652-01",name:"Krupp Brothers",city:"Napa",state:"CA",approved:"2025-12-01",url:"https://www.kruppbrothers.com",local:false,v:["Cabernet Sauvignon","Zinfandel","Merlot"]},
  {id:77,permit:"26653-01",name:"Redmon Wines",city:"Napa",state:"CA",approved:"2025-12-01",url:"https://www.redmonwines.com",local:false,v:[]},
  {id:78,permit:"26655-01",name:"Keuka Spring Vineyards",city:"Penn Yan",state:"NY",approved:"2025-12-01",url:"https://www.keukaspringvineyards.com",local:false,v:["Riesling","Cabernet Franc","Chardonnay"]},
  {id:79,permit:"26656-01",name:"Bricoleur Vineyards",city:"Windsor",state:"CA",approved:"2025-12-01",url:"https://www.bricoleurvineyards.com",local:false,v:["Chardonnay","Pinot Noir","Rosé","Sparkling"]},
  {id:80,permit:"26657-01",name:"Aaron Wines",city:"Paso Robles",state:"CA",approved:"2025-12-01",url:"https://aaronwines.com",local:false,v:[]},
  {id:81,permit:"26658-01",name:"Glenlyon Winery",city:"Glen Ellen",state:"CA",approved:"2025-12-01",url:"https://www.glenlyonwinery.com",local:false,v:[]},
  {id:82,permit:"26659-01",name:"North Coast Wine Co.",city:"Geyersville",state:"CA",approved:"2025-12-01",url:"https://northcoastwine.com",local:false,v:[]},
  {id:83,permit:"26660-01",name:"Wild Sun Winery",city:"Hillsboro",state:"MO",approved:"2025-12-01",url:"https://www.wildsunwinery.com",local:false,v:["Norton","Chambourcin","Chardonel","Sparkling"]},
  {id:84,permit:"26671-01",name:"Johnson Estate Winery",city:"Westfield",state:"NY",approved:"2025-12-08",url:"https://www.johnsonwinery.com",local:false,v:["Riesling","Cabernet Franc","Chardonnay","Concord"]},
  {id:85,permit:"26672-01",name:"Ovid Napa Valley",city:"St. Helena",state:"CA",approved:"2025-12-08",url:"https://www.ovidnapavalley.com",local:false,v:["Proprietary Red","Hexameter","Sumo"]},
  {id:86,permit:"26704-01",name:"Raen Wines",city:"Sebastopol",state:"CA",approved:"2025-12-15",url:"https://www.raenwine.com",local:false,v:["Pinot Noir","Chardonnay"]},
  {id:87,permit:"26707-01",name:"St. Supery Estate Vineyards",city:"Rutherford",state:"CA",approved:"2025-12-15",url:"https://www.stsupery.com",local:false,v:["Cabernet Sauvignon","Sauvignon Blanc","Chardonnay","Merlot"]},
  {id:88,permit:"26723-01",name:"Stone Hill Winery",city:"Hermann",state:"MO",approved:"2025-12-29",url:"https://www.stonehillwinery.com",local:false,v:["Norton","Vignoles","Chardonel","Port"]},
  // Jan 2026
  {id:89,permit:"02671-01",name:"Post Winery",city:"Altus",state:"AR",approved:"2025-08-05",url:"http://postwinery.com",local:true,v:["Muscadine Red","Muscadine White","Muscadine Pink","Sparkling"]},
  {id:90,permit:"26746-01",name:"Sojourn Cellars",city:"Santa Rosa",state:"CA",approved:"2026-01-12",url:"https://www.sojourncellars.com",local:false,v:["Pinot Noir","Cabernet Sauvignon","Chardonnay"]},
  {id:91,permit:"26747-01",name:"Rutherford Wine Company",city:"St. Helena",state:"CA",approved:"2026-01-12",url:"https://rutherfordwine.com",local:false,v:["Cabernet Sauvignon","Merlot","Chardonnay"]},
  {id:92,permit:"26756-01",name:"Barnett Vineyards",city:"St. Helena",state:"CA",approved:"2026-01-20",url:"https://www.barnettvineyards.com",local:false,v:["Cabernet Sauvignon","Pinot Noir","Chardonnay"]},
  {id:93,permit:"26774-01",name:"Waterbrook Winery",city:"Walla Walla",state:"WA",approved:"2026-01-22",url:"https://www.waterbrook.com",local:false,v:["Merlot","Cabernet Sauvignon","Sauvignon Blanc","Chardonnay"]},
  {id:94,permit:"26775-01",name:"Ste. Chapelle Winery",city:"Caldwell",state:"ID",approved:"2026-01-22",url:"https://www.stechapelle.com",local:false,v:["Riesling","Chardonnay","Merlot","Gewürztraminer"]},
  {id:95,permit:"26776-01",name:"Gruet Winery",city:"Albuquerque",state:"NM",approved:"2026-01-22",url:"https://www.gruetwinery.com",local:false,v:["Brut NV","Blanc de Blancs","Blanc de Noirs","Demi-Sec"]},
  // Feb 2026
  {id:96,permit:"26793-01",name:"Saxum Vineyards",city:"Paso Robles",state:"CA",approved:"2026-02-03",url:"https://www.saxumvineyards.com",local:false,v:["Rhône Blends","Syrah","Grenache","Mourvèdre"]},
  {id:97,permit:"26795-01",name:"Dry Farm Wines",city:"Dallas",state:"TX",approved:"2026-02-03",url:"https://www.dryfarmwines.com",local:false,v:["Various (Organic/Biodynamic)"]},
  {id:98,permit:"26819-01",name:"Davis Estates",city:"Calistoga",state:"CA",approved:"2026-02-09",url:"https://www.davisestates.com",local:false,v:["Cabernet Sauvignon","Chardonnay","Grenache"]},
  {id:99,permit:"26843-01",name:"Adelsheim Vineyard",city:"Newberg",state:"OR",approved:"2026-02-17",url:"https://www.adelsheim.com",local:false,v:["Pinot Noir","Chardonnay","Pinot Gris","Pinot Blanc"]},
  {id:100,permit:"26844-01",name:"Patricia Green Cellars",city:"Newberg",state:"OR",approved:"2026-02-17",url:"https://www.patriciagreencellars.com",local:false,v:["Pinot Noir"]},
  {id:101,permit:"26845-01",name:"D.R. Stephens Estate",city:"St. Helena",state:"CA",approved:"2026-02-17",url:null,local:false,v:["Cabernet Sauvignon"]},
  {id:102,permit:"26857-01",name:"Sokol Blosser Winery",city:"Dayton",state:"OR",approved:"2026-02-23",url:"https://www.sokolblosser.com",local:false,v:["Pinot Noir","Pinot Gris","Rosé"]},
  {id:103,permit:"26858-01",name:"Deane and Hoyle Brands",city:"Stonewall",state:"TX",approved:"2026-02-23",url:null,local:false,v:[]},
  // Mar 2026
  {id:104,permit:"26877-01",name:"PlumpJack Winery",city:"Oakville",state:"CA",approved:"2026-03-02",url:"https://www.plumpjackwinery.com",local:false,v:["Cabernet Sauvignon","Chardonnay","Merlot"]},
  {id:105,permit:"26889-01",name:"Halter Ranch Vineyard",city:"Paso Robles",state:"CA",approved:"2026-03-09",url:"https://www.halterranch.com",local:false,v:["Grenache","Syrah","Mourvèdre","Cabernet Sauvignon"]},
  {id:106,permit:"26893-01",name:"Vinfillment",city:"American Canyon",state:"CA",approved:"2026-03-09",url:"https://www.vinfillment.com",local:false,v:[]},
  {id:107,permit:"26897-01",name:"Wine Gift Shop",city:"Calistoga",state:"CA",approved:"2026-03-09",url:"https://winegiftshop.com",local:false,v:[]},
  {id:108,permit:"26898-01",name:"Small Lot Bottles",city:"Brownfield",state:"TX",approved:"2026-03-09",url:"https://www.smalllotbottles.com",local:false,v:[]},
  {id:109,permit:"26900-01",name:"King Estate Winery",city:"Eugene",state:"OR",approved:"2026-03-09",url:"https://www.kingestate.com",local:false,v:["Pinot Noir","Pinot Gris","Chardonnay"]},
  {id:110,permit:"26920-01",name:"Colgin Cellars",city:"St. Helena",state:"CA",approved:"2026-03-16",url:"https://www.colgincellars.com",local:false,v:["Cabernet Sauvignon","Proprietary Blends"]},
  {id:111,permit:"26921-01",name:"Patent Wines",city:"Oakville",state:"CA",approved:"2026-03-16",url:"https://www.patentwines.com",local:false,v:[]},
  {id:112,permit:"26952-01",name:"Robert Mondavi Winery",city:"Oakville",state:"CA",approved:"2026-03-30",url:"https://www.robertmondaviwinery.com",local:false,v:["Cabernet Sauvignon","Chardonnay","Fumé Blanc","Pinot Noir"]},
  {id:113,permit:"26953-01",name:"Stonewall Canyon Winery",city:"Soledad",state:"CA",approved:"2026-03-30",url:null,local:false,v:[]},
  {id:114,permit:"26954-01",name:"The Prisoner Wine Company",city:"Rutherford",state:"CA",approved:"2026-03-30",url:"https://www.theprisonerwinecompany.com",local:false,v:["Red Blend","Cabernet Sauvignon","Chardonnay","Rosé"]},
  {id:115,permit:"26955-01",name:"Lingua Franca",city:"Salem",state:"OR",approved:"2026-03-30",url:"https://www.linguafrancawine.com",local:false,v:["Pinot Noir","Chardonnay"]},
  {id:116,permit:"26956-01",name:"Sea Smoke Cellars",city:"Lompoc",state:"CA",approved:"2026-03-30",url:"https://www.seasmoke.com",local:false,v:["Pinot Noir"]},
  {id:117,permit:"26958-01",name:"Buehler Vineyards",city:"St. Helena",state:"CA",approved:"2026-03-30",url:"https://www.buehlervineyards.com",local:false,v:["Cabernet Sauvignon","Zinfandel","Chardonnay","White Zinfandel"]},
  {id:118,permit:"26964-01",name:"Schrader Cellars",city:"Oakville",state:"CA",approved:"2026-03-30",url:"https://www.schradercellars.com",local:false,v:["Cabernet Sauvignon"]},
  // Apr 2026
  {id:119,permit:"27001-01",name:"Bellavini Winery",city:"Ukiah",state:"CA",approved:"2026-04-06",url:null,local:false,v:[]},
  {id:120,permit:"27055-01",name:"Linne Calodo Cellars",city:"Paso Robles",state:"CA",approved:"2026-04-20",url:"https://www.linnecalodo.com",local:false,v:["Syrah","Grenache","Zinfandel","Rhône Blends"]},
  {id:121,permit:"27067-01",name:"Rasa Vineyards",city:"Walla Walla",state:"WA",approved:"2026-04-27",url:"https://www.rasavineyards.com",local:false,v:["Cabernet Sauvignon","Syrah","Rosé"]},
];

const STATE_LABELS = {
  AR:"Arkansas",CA:"California",OR:"Oregon",WA:"Washington",NC:"North Carolina",
  NM:"New Mexico",ID:"Idaho",TX:"Texas",MO:"Missouri",NY:"New York",OK:"Oklahoma",WY:"Wyoming"
};
const SC = {
  AR:"#2d6a4f",CA:"#722f37",OR:"#1a6b8a",WA:"#2d5a8a",NC:"#8a2d2d",
  NM:"#8a6b2d",ID:"#4a7c2d",TX:"#8a6020",MO:"#5a3070",NY:"#2d6070",OK:"#706020",WY:"#207060"
};

const fmt = d => new Date(d).toLocaleDateString("en-US",{month:"short",day:"numeric",year:"numeric"});
const PER_PAGE = 24;

function AgeGate({onConfirm}) {
  const [denied,setDenied] = useState(false);
  return (
    <div style={{position:"fixed",inset:0,background:"#100306",display:"flex",alignItems:"center",justifyContent:"center",zIndex:9999,fontFamily:"'Lato',sans-serif"}}>
      <style>{GF}</style>
      <div style={{position:"absolute",inset:0,background:"radial-gradient(ellipse at 40% 55%,rgba(114,47,55,0.22) 0%,transparent 58%),radial-gradient(ellipse at 70% 35%,rgba(201,168,76,0.07) 0%,transparent 50%)"}}/>
      <div style={{textAlign:"center",padding:"3rem 2.5rem",maxWidth:440,position:"relative",zIndex:1}}>
        <div style={{width:68,height:68,borderRadius:"50%",background:"rgba(114,47,55,0.25)",border:"1px solid rgba(201,168,76,0.25)",display:"flex",alignItems:"center",justifyContent:"center",fontSize:28,margin:"0 auto 1.5rem"}}>🍷</div>
        <div style={{fontFamily:"'Lato',sans-serif",color:"#c9a84c",fontSize:10,letterSpacing:6,textTransform:"uppercase",marginBottom:"0.75rem"}}>Welcome to</div>
        <h1 style={{fontFamily:"'Playfair Display',serif",color:"#fdfaf6",fontSize:42,fontWeight:700,margin:"0 0 0.25rem",lineHeight:1.1}}>WineDown<br/><em style={{color:"#c9a84c",fontWeight:400}}>Arkansas</em></h1>
        <div style={{width:40,height:1,background:"linear-gradient(90deg,transparent,#c9a84c,transparent)",margin:"1.25rem auto"}}/>
        <p style={{color:"#6a4040",fontSize:13,marginBottom:"2.5rem",lineHeight:1.8}}>Tracking every winery licensed to ship directly to your Arkansas door.</p>
        {!denied ? <>
          <p style={{color:"#c4a0a0",fontSize:15,marginBottom:"1.75rem",fontFamily:"'Playfair Display',serif",fontStyle:"italic"}}>Are you 21 years of age or older?</p>
          <div style={{display:"flex",gap:14,justifyContent:"center"}}>
            <button onClick={onConfirm} style={{background:"#722f37",color:"#fdfaf6",border:"none",padding:"13px 42px",fontSize:11,fontFamily:"'Lato',sans-serif",fontWeight:700,letterSpacing:3,textTransform:"uppercase",cursor:"pointer",borderRadius:1}}>Yes, Enter</button>
            <button onClick={()=>setDenied(true)} style={{background:"transparent",color:"#4a2020",border:"1px solid #2d1010",padding:"13px 42px",fontSize:11,fontFamily:"'Lato',sans-serif",fontWeight:700,letterSpacing:3,textTransform:"uppercase",cursor:"pointer",borderRadius:1}}>No</button>
          </div>
        </> :
          <div style={{background:"#1a0608",border:"1px solid #3d1010",borderRadius:2,padding:"1.5rem"}}>
            <p style={{color:"#c9a84c",fontSize:13,margin:0,lineHeight:1.8}}>We're sorry — you must be 21 or older to visit this site. Please return when you are of legal drinking age.</p>
          </div>
        }
        <p style={{color:"#1a0608",fontSize:10,marginTop:"2.5rem",letterSpacing:2,textTransform:"uppercase"}}>Please Drink Responsibly · Must Be 21+</p>
      </div>
    </div>
  );
}

function Header() {
  return (
    <header style={{background:"#100306",padding:"0 2rem",display:"flex",alignItems:"center",justifyContent:"space-between",height:58,borderBottom:"1px solid #200810",position:"sticky",top:0,zIndex:100}}>
      <div style={{display:"flex",alignItems:"center",gap:9}}>
        <span style={{fontSize:17}}>🍷</span>
        <span style={{fontFamily:"'Playfair Display',serif",color:"#fdfaf6",fontSize:16,fontWeight:700}}>WineDown</span>
        <span style={{fontFamily:"'Playfair Display',serif",color:"#c9a84c",fontSize:16,fontWeight:400,fontStyle:"italic"}}>Arkansas</span>
      </div>
      <nav style={{display:"flex",gap:"1.5rem",alignItems:"center"}}>
        <a href="#directory" style={{color:"#6a3030",fontSize:10,fontFamily:"'Lato',sans-serif",letterSpacing:2,textTransform:"uppercase",textDecoration:"none"}}>Directory</a>
        <a href="#about" style={{color:"#6a3030",fontSize:10,fontFamily:"'Lato',sans-serif",letterSpacing:2,textTransform:"uppercase",textDecoration:"none"}}>How It Works</a>
        <button style={{background:"#722f37",color:"#fdfaf6",border:"none",padding:"7px 16px",fontSize:10,fontFamily:"'Lato',sans-serif",fontWeight:700,letterSpacing:2,textTransform:"uppercase",cursor:"pointer",borderRadius:1}}>Newsletter</button>
      </nav>
    </header>
  );
}

function Hero({count}) {
  return (
    <div style={{background:"#100306",padding:"5rem 2rem 4.5rem",textAlign:"center",position:"relative",overflow:"hidden"}}>
      <div style={{position:"absolute",inset:0,background:"radial-gradient(ellipse at 30% 60%,rgba(114,47,55,0.22) 0%,transparent 55%),radial-gradient(ellipse at 72% 40%,rgba(201,168,76,0.07) 0%,transparent 50%)"}}/>
      <div style={{position:"relative",maxWidth:660,margin:"0 auto"}}>
        <div style={{fontFamily:"'Lato',sans-serif",color:"#c9a84c",fontSize:10,letterSpacing:6,textTransform:"uppercase",marginBottom:"1.25rem"}}>Arkansas Direct-to-Consumer Wine Shipping · Est. 2025</div>
        <h1 style={{fontFamily:"'Playfair Display',serif",color:"#fdfaf6",fontSize:52,fontWeight:700,margin:"0 0 1.5rem",lineHeight:1.1}}>Your door.<br/><em style={{color:"#c9a84c",fontWeight:400}}>Their vineyard.</em></h1>
        <div style={{width:46,height:1,background:"linear-gradient(90deg,transparent,#c9a84c55,transparent)",margin:"0 auto 1.75rem"}}/>
        <p style={{color:"#6a4040",fontSize:15,margin:"0 auto 2.75rem",lineHeight:1.85,fontFamily:"'Lato',sans-serif",fontWeight:300}}>Arkansas now allows wineries to ship wine directly to your home. We track every licensed shipper — verified against state ABC records — so you can shop with confidence.</p>
        <a href="#directory" style={{background:"#722f37",color:"#fdfaf6",padding:"12px 28px",fontSize:10,fontFamily:"'Lato',sans-serif",fontWeight:700,letterSpacing:3,textTransform:"uppercase",textDecoration:"none",borderRadius:1,display:"inline-block"}}>Browse All {count} Wineries</a>
      </div>
    </div>
  );
}

function StatsBar({wineries}) {
  const states = [...new Set(wineries.map(w=>w.state))].length;
  const stats = [
    {v:wineries.length,l:"Licensed Wineries"},
    {v:states,l:"States Represented"},
    {v:wineries.filter(w=>w.local).length,l:"Arkansas Wineries"},
    {v:"Jun 30",l:"Annual Renewal Date"},
  ];
  return (
    <div style={{background:"#fdfaf6",borderBottom:"1px solid #e8ddd0",display:"grid",gridTemplateColumns:"repeat(4,1fr)"}}>
      {stats.map((s,i)=>(
        <div key={i} style={{textAlign:"center",padding:"1.5rem 1rem",borderRight:i<3?"1px solid #e8ddd0":"none"}}>
          <div style={{fontFamily:"'Playfair Display',serif",color:"#722f37",fontSize:32,fontWeight:700,lineHeight:1}}>{s.v}</div>
          <div style={{fontFamily:"'Lato',sans-serif",color:"#9a7070",fontSize:10,letterSpacing:2.5,textTransform:"uppercase",marginTop:6}}>{s.l}</div>
        </div>
      ))}
    </div>
  );
}

function WineryCard({w}) {
  const c = SC[w.state]||"#722f37";
  const monthAdded = new Date(w.approved).toLocaleDateString("en-US",{month:"short",year:"numeric"});
  return (
    <div style={{background:"#fff",border:"1px solid #e8ddd0",borderRadius:2,overflow:"hidden",display:"flex",flexDirection:"column",transition:"box-shadow 0.15s"}}
      onMouseEnter={e=>e.currentTarget.style.boxShadow="0 5px 24px rgba(114,47,55,0.10)"}
      onMouseLeave={e=>e.currentTarget.style.boxShadow=""}>
      <div style={{background:"linear-gradient(135deg,#100306,#1e080e)",padding:"1.1rem 1.1rem 0.9rem",position:"relative"}}>
        {w.local && <span style={{position:"absolute",top:9,right:9,background:"rgba(201,168,76,0.12)",color:"#c9a84c",fontSize:9,fontFamily:"'Lato',sans-serif",fontWeight:700,letterSpacing:2,padding:"2px 7px",borderRadius:1,border:"1px solid rgba(201,168,76,0.3)",textTransform:"uppercase"}}>Local</span>}
        <div style={{display:"flex",alignItems:"center",gap:9,paddingRight:w.local?52:0,marginBottom:"0.75rem"}}>
          <div style={{width:30,height:30,borderRadius:"50%",background:c+"1a",border:`1px solid ${c}44`,display:"flex",alignItems:"center",justifyContent:"center",fontSize:9,fontFamily:"'Lato',sans-serif",fontWeight:700,color:c,flexShrink:0}}>{w.state}</div>
          <div>
            <div style={{fontFamily:"'Playfair Display',serif",color:"#fdfaf6",fontSize:13,fontWeight:600,lineHeight:1.25}}>{w.name}</div>
            <div style={{color:"#6a4040",fontSize:11,fontFamily:"'Lato',sans-serif",marginTop:2}}>{w.city}, {STATE_LABELS[w.state]||w.state}</div>
          </div>
        </div>
        {w.v && w.v.length > 0 && (
          <div style={{display:"flex",flexWrap:"wrap",gap:4}}>
            {w.v.slice(0,4).map((varietal,i)=>(
              <span key={i} style={{background:"#ffffff0d",color:"#c4a0a0",fontSize:9,fontFamily:"'Lato',sans-serif",padding:"2px 7px",borderRadius:1,border:"1px solid #ffffff14",whiteSpace:"nowrap"}}>{varietal}</span>
            ))}
          </div>
        )}
      </div>
      <div style={{padding:"0.75rem 1.1rem",background:"#fdfaf6",borderTop:"1px solid #e8ddd0",display:"flex",justifyContent:"space-between",alignItems:"center"}}>
        <div>
          <div style={{fontFamily:"'Lato',sans-serif",color:"#b09090",fontSize:9,letterSpacing:1.5,textTransform:"uppercase"}}>Permit</div>
          <div style={{fontFamily:"'Lato',sans-serif",color:"#3a1a1a",fontSize:11,fontWeight:700,marginTop:1}}>{w.permit}</div>
        </div>
        <div style={{textAlign:"center"}}>
          <div style={{fontFamily:"'Lato',sans-serif",color:"#b09090",fontSize:9,letterSpacing:1.5,textTransform:"uppercase"}}>Licensed</div>
          <div style={{fontFamily:"'Lato',sans-serif",color:"#3a1a1a",fontSize:11,marginTop:1}}>{monthAdded}</div>
        </div>
        <div style={{display:"flex",alignItems:"center",gap:4}}>
          <div style={{width:5,height:5,borderRadius:"50%",background:"#2d6a4f"}}/>
          <span style={{fontFamily:"'Lato',sans-serif",color:"#2d6a4f",fontSize:10,fontWeight:700,letterSpacing:1.5,textTransform:"uppercase"}}>Active</span>
        </div>
      </div>
      {w.url && (
        <div style={{padding:"0 1.1rem 0.75rem",background:"#fdfaf6"}}>
          <a href={w.url} target="_blank" rel="noopener noreferrer" style={{display:"block",background:"#722f37",color:"#fdfaf6",padding:"7px 0",fontSize:10,fontFamily:"'Lato',sans-serif",fontWeight:700,letterSpacing:2,textTransform:"uppercase",textDecoration:"none",textAlign:"center",borderRadius:1}}>Visit Website</a>
        </div>
      )}
    </div>
  );
}

function Directory({wineries}) {
  const [search,setSearch] = useState("");
  const [stateFilter,setStateFilter] = useState("All");
  const [sort,setSort] = useState("newest");
  const [page,setPage] = useState(1);

  const states = ["All",...[...new Set(wineries.map(w=>w.state))].sort()];

  const filtered = wineries
    .filter(w=>{
      const q=search.toLowerCase();
      const m=w.name.toLowerCase().includes(q)||w.city.toLowerCase().includes(q)||(STATE_LABELS[w.state]||"").toLowerCase().includes(q)||w.permit.includes(q)||w.v.join(" ").toLowerCase().includes(q);
      const sf=stateFilter==="All"||w.state===stateFilter;
      return m&&sf;
    })
    .sort((a,b)=>sort==="newest"?new Date(b.approved)-new Date(a.approved):new Date(a.approved)-new Date(b.approved));

  const totalPages=Math.ceil(filtered.length/PER_PAGE);
  const pageItems=filtered.slice((page-1)*PER_PAGE,page*PER_PAGE);

  return (
    <div id="directory" style={{background:"#f5ede6",padding:"3.5rem 2rem"}}>
      <div style={{maxWidth:1200,margin:"0 auto"}}>
        <div style={{marginBottom:"2rem"}}>
          <div style={{fontFamily:"'Lato',sans-serif",color:"#c9a84c",fontSize:10,letterSpacing:5,textTransform:"uppercase",marginBottom:"0.5rem"}}>The Directory</div>
          <h2 style={{fontFamily:"'Playfair Display',serif",color:"#1a0608",fontSize:30,fontWeight:700,margin:"0 0 0.4rem"}}>Licensed Direct Shippers</h2>
          <p style={{fontFamily:"'Lato',sans-serif",color:"#9a7070",fontSize:12,margin:0}}>Verified against Arkansas ABC permit records. Permits renew annually on June 30.</p>
        </div>
        <div style={{display:"flex",gap:10,marginBottom:"1rem",flexWrap:"wrap",alignItems:"center"}}>
          <input value={search} onChange={e=>{setSearch(e.target.value);setPage(1);}} placeholder="Search winery, city, state, varietal, or permit #..." style={{flex:1,minWidth:220,padding:"9px 13px",fontFamily:"'Lato',sans-serif",fontSize:12,border:"1px solid #d4bfb0",borderRadius:1,background:"#fff",color:"#1a0608",outline:"none"}}/>
          <select value={stateFilter} onChange={e=>{setStateFilter(e.target.value);setPage(1);}} style={{padding:"9px 12px",fontFamily:"'Lato',sans-serif",fontSize:12,border:"1px solid #d4bfb0",borderRadius:1,background:"#fff",color:"#1a0608",outline:"none",cursor:"pointer"}}>
            {states.map(s=><option key={s} value={s}>{s==="All"?"All States":STATE_LABELS[s]||s}</option>)}
          </select>
          <select value={sort} onChange={e=>{setSort(e.target.value);setPage(1);}} style={{padding:"9px 12px",fontFamily:"'Lato',sans-serif",fontSize:12,border:"1px solid #d4bfb0",borderRadius:1,background:"#fff",color:"#1a0608",outline:"none",cursor:"pointer"}}>
            <option value="newest">Newest First</option>
            <option value="oldest">Oldest First</option>
          </select>
        </div>
        <div style={{fontFamily:"'Lato',sans-serif",color:"#9a7070",fontSize:12,marginBottom:"1rem"}}>
          Showing {filtered.length===0?"0":`${(page-1)*PER_PAGE+1}–${Math.min(page*PER_PAGE,filtered.length)}`} of {filtered.length} {filtered.length===1?"winery":"wineries"}
        </div>
        {pageItems.length>0 ? (
          <div style={{display:"grid",gridTemplateColumns:"repeat(auto-fill,minmax(240px,1fr))",gap:14}}>
            {pageItems.map(w=><WineryCard key={w.id} w={w}/>)}
          </div>
        ) : (
          <div style={{textAlign:"center",padding:"4rem 2rem",color:"#9a7070",fontFamily:"'Playfair Display',serif",fontSize:18,fontStyle:"italic"}}>No wineries match your search.</div>
        )}
        {totalPages>1 && (
          <div style={{display:"flex",alignItems:"center",justifyContent:"center",gap:12,marginTop:"2rem"}}>
            <button onClick={()=>setPage(p=>Math.max(1,p-1))} disabled={page===1} style={{background:page===1?"#e8ddd0":"#722f37",color:page===1?"#b09090":"#fdfaf6",border:"none",padding:"8px 18px",fontSize:11,fontFamily:"'Lato',sans-serif",fontWeight:700,letterSpacing:2,textTransform:"uppercase",cursor:page===1?"not-allowed":"pointer",borderRadius:1}}>← Prev</button>
            <span style={{fontFamily:"'Lato',sans-serif",color:"#6a4040",fontSize:12}}>Page {page} of {totalPages}</span>
            <button onClick={()=>setPage(p=>Math.min(totalPages,p+1))} disabled={page===totalPages} style={{background:page===totalPages?"#e8ddd0":"#722f37",color:page===totalPages?"#b09090":"#fdfaf6",border:"none",padding:"8px 18px",fontSize:11,fontFamily:"'Lato',sans-serif",fontWeight:700,letterSpacing:2,textTransform:"uppercase",cursor:page===totalPages?"not-allowed":"pointer",borderRadius:1}}>Next →</button>
          </div>
        )}
        <p style={{fontFamily:"'Lato',sans-serif",color:"#c9a84c",fontSize:11,marginTop:"1.5rem",textAlign:"center",letterSpacing:1}}>
          ⚠ Wine may only ship to wet areas of Arkansas. <a href="https://gis.arkansas.gov/product/abc-wet-and-dry-areas/" target="_blank" rel="noopener noreferrer" style={{color:"#722f37"}}>Verify your area →</a>
        </p>
      </div>
    </div>
  );
}

function HowItWorks() {
  return (
    <div id="about" style={{background:"#100306",padding:"4rem 2rem",borderTop:"1px solid #1a0608"}}>
      <div style={{maxWidth:860,margin:"0 auto",textAlign:"center"}}>
        <div style={{fontFamily:"'Lato',sans-serif",color:"#c9a84c",fontSize:10,letterSpacing:5,textTransform:"uppercase",marginBottom:"0.75rem"}}>How It Works</div>
        <h2 style={{fontFamily:"'Playfair Display',serif",color:"#fdfaf6",fontSize:28,fontWeight:700,margin:"0 0 3rem"}}>Simple. Accurate. Always Current.</h2>
        <div style={{display:"grid",gridTemplateColumns:"repeat(3,1fr)",gap:18}}>
          {[
            {i:"🔎",t:"We Watch for Changes",d:"Our system monitors Arkansas state alcohol licensing records on a regular schedule, automatically identifying when new wine shipping authorizations are issued."},
            {i:"✅",t:"We Verify Active Status",d:"Each permit is cross-referenced against the state's full active license database to confirm the winery holds a current, valid authorization to ship directly to Arkansas consumers."},
            {i:"🍾",t:"You Shop with Confidence",d:"Browse our verified directory, click through to a winery's website, and have wine shipped to your door — up to 24 cases per year, in eligible Arkansas zip codes."},
          ].map((s,i)=>(
            <div key={i} style={{background:"#1a0608",border:"1px solid #2d1010",borderRadius:2,padding:"1.75rem 1.4rem",textAlign:"left"}}>
              <div style={{fontSize:26,marginBottom:"0.9rem"}}>{s.i}</div>
              <h3 style={{fontFamily:"'Playfair Display',serif",color:"#c9a84c",fontSize:16,fontWeight:600,margin:"0 0 0.7rem"}}>{s.t}</h3>
              <p style={{fontFamily:"'Lato',sans-serif",color:"#4a2020",fontSize:13,lineHeight:1.75,margin:0}}>{s.d}</p>
            </div>
          ))}
        </div>
        <div style={{marginTop:"2.5rem",background:"#1a0608",border:"1px solid rgba(201,168,76,0.2)",borderRadius:2,padding:"1.25rem 2rem"}}>
          <p style={{fontFamily:"'Lato',sans-serif",color:"#6a4040",fontSize:13,margin:0,lineHeight:1.7}}>
            <span style={{color:"#c9a84c",fontWeight:700}}>Important:</span> Wine may only ship to wet areas of Arkansas. 29 counties are fully dry and some have mixed areas. <a href="https://gis.arkansas.gov/product/abc-wet-and-dry-areas/" target="_blank" rel="noopener noreferrer" style={{color:"#c9a84c"}}>Check your area →</a>
          </p>
        </div>
      </div>
    </div>
  );
}

function Footer() {
  return (
    <footer style={{background:"#080103",padding:"2.5rem 2rem",textAlign:"center",borderTop:"1px solid #1a0608"}}>
      <div style={{fontFamily:"'Playfair Display',serif",color:"#c9a84c",fontSize:14,marginBottom:"0.5rem"}}>🍷 WineDown Arkansas</div>
      <p style={{fontFamily:"'Lato',sans-serif",color:"#2d1010",fontSize:11,margin:"0 0 0.75rem",lineHeight:1.7}}>Permit data sourced from the Arkansas Department of Finance & Administration, Alcoholic Beverage Control Division.<br/>WineDown Arkansas is an independent information service and is not affiliated with the state of Arkansas.</p>
      <p style={{fontFamily:"'Lato',sans-serif",color:"#1a0608",fontSize:10,letterSpacing:2,margin:0,textTransform:"uppercase"}}>© 2026 WineDown Arkansas · Must Be 21+ · Please Drink Responsibly</p>
    </footer>
  );
}

export default function App() {
  const [v,setV] = useState(false);
  return (<>
    <style>{GF}</style>
    {!v && <AgeGate onConfirm={()=>setV(true)}/>}
    {v && <div style={{fontFamily:"'Lato',sans-serif"}}><Header/><Hero count={WINERIES.length}/><StatsBar wineries={WINERIES}/><Directory wineries={WINERIES}/><HowItWorks/><Footer/></div>}
  </>);
}
