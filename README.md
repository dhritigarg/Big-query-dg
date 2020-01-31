# Big-query-dg

Based ON : NYC Street Trees

1. What are the 5 most common tree species in New York City?

SELECT
  spc_latin,
  spc_common,
  COUNT(*) AS count
FROM
  `bigquery-public-data.new_york.tree_census_2015`
WHERE
  status="Alive"
GROUP BY
  spc_latin,
  spc_common
ORDER BY
  count DESC limit 5

Output:

spc_latin	spc_common	count
Platanus x acerifolia	London planetree	87014
Gleditsia triacanthos var. inermis	honeylocust	64263
Pyrus calleryana	Callery pear	58931
Quercus palustris	pin oak	53185
Acer platanoides	Norway maple	34189


2. What is the percentage of healthy trees of each species?

SELECT
  spc_latin,
  spc_common,
  ROUND(COUNTIF(health="Good")/COUNT(*)*100) AS healthy_pct
FROM
  `bigquery-public-data.new_york.tree_census_2015`
WHERE
  status="Alive"
GROUP BY
  spc_latin,
  spc_common

Output:

spc_latin	spc_common	healthy_pct
Quercus palustris	pin oak	86.0
Pyrus calleryana	Callery pear	82.0
Tilia cordata	littleleaf linden	79.0
Gleditsia triacanthos var. inermis	honeylocust	85.0
Styphnolobium japonicum	Sophora	82.0
Zelkova serrata	Japanese zelkova	86.0
Platanus x acerifolia	London planetree	84.0
Quercus velutina	black oak	82.0
Tilia americana	American linden	80.0
Acer ginnala	Amur maple	80.0
Ginkgo biloba	ginkgo	81.0
Acer rubrum	red maple	78.0
Carpinus betulus	European hornbeam	80.0
Prunus virginiana	'Schubert' chokecherry	80.0
Quercus robur	English oak	83.0
Koelreuteria paniculata	golden raintree	83.0
Prunus	cherry	84.0
Quercus bicolor	swamp white oak	82.0
Ulmus americana	American elm	80.0
Populus grandidentata	bigtooth aspen	69.0
Liquidambar styraciflua	sweetgum	85.0
Ulmus parvifolia	Chinese elm	84.0
Gymnocladus dioicus	Kentucky coffeetree	84.0
Quercus phellos	willow oak	86.0
Celtis occidentalis	common hackberry	78.0
Betula nigra	river birch	81.0
Prunus cerasifera	purple-leaf plum	79.0
Acer	maple	66.0
Juniperus virginiana	eastern redcedar	86.0
Ostrya virginiana	American hophornbeam	80.0
Quercus acutissima	sawtooth oak	88.0
Eucommia ulmoides	hardy rubber tree	81.0
Metasequoia glyptostroboides	dawn redwood	80.0
Salix babylonica	weeping willow	77.0
Betula papyrifera	paper birch	79.0
Carpinus caroliniana	American hornbeam	80.0
Quercus rubra	northern red oak	81.0
Tilia tomentosa	silver linden	85.0
Quercus imbricaria	shingle oak	84.0
Fagus grandifolia	American beech	78.0
Quercus shumardii	Schumard's oak	80.0
Fraxinus pennsylvanica	green ash	81.0
Chionanthus retusus	Chinese fringetree	87.0
Quercus alba	white oak	79.0
Magnolia grandiflora	southern magnolia	86.0
Quercus macrocarpa	bur oak	78.0
Cercis reniformis	Oklahoma redbud	79.0
Acer griseum	paperbark maple	72.0
Robinia pseudoacacia	black locust	78.0
Prunus serotina	black cherry	76.0
Ailanthus altissima	tree of heaven	71.0
Syringa pekinensis	Chinese tree lilac	81.0
Cercis canadensis	eastern redbud	77.0
Fraxinus	ash	81.0
Syringa reticulata	Japanese tree lilac	80.0
Taxodium distichum	bald cypress	81.0
Carpinus japonica	Japanese hornbeam	79.0
Acer palmatum	Japanese maple	79.0
Populus deltoides	eastern cottonwood	76.0
Cornus alternifolia	pagoda dogwood	78.0
Cornus florida	flowering dogwood	76.0
Acer platanoides	Norway maple	62.0
Betula pendula	silver birch	75.0
Malus	crab apple	82.0
Castanea mollissima	Chinese chestnut	87.0
Taxodium ascendens	pond cypress	65.0
Crataegus	hawthorn	78.0
Acer pseudoplatanus	sycamore maple	73.0
Maackia amurensis	Amur maackia	82.0
Acer saccharinum	silver maple	77.0
Corylus colurna	Turkish hazelnut	70.0
Fraxinus americana	white ash	80.0
Magnolia acuminata	cucumber magnolia	84.0
Ilex	holly	86.0
Quercus coccinea	scarlet oak	74.0
Nyssa sylvatica	blackgum	77.0
Cladrastis kentukea	Kentucky yellowwood	77.0
Amelanchier	serviceberry	80.0
Cercidiphyllum japonicum	katsura tree	64.0
Morus	mulberry	76.0
Ulmus pumila	Siberian elm	80.0
Acer saccharum	sugar maple	70.0
Cotinus coggygria	smoketree	81.0
Albizia julibrissin	mimosa	80.0
Cornus mas	Cornelian cherry	83.0
Paulownia tomentosa	empress tree	73.0
Cornus kousa	kousa dogwood	78.0
Quercus falcata	southern red oak	80.0
Acer campestre	hedge maple	82.0
Crataegus crusgalli var. inermis	cockspur hawthorn	78.0
Acer tataricum	tartar maple	75.0
Pinus virginiana	Virginia pine	80.0
Pinus sylvestris	Scots pine	84.0
Catalpa	catalpa	68.0
Parrotia persica	Persian ironwood	79.0
Juglans nigra	black walnut	79.0
Liriodendron tulipifera	tulip-poplar	75.0
Sassafras albidum	sassafras	75.0
Styrax japonicus	Japanese snowbell	76.0
Aesculus hippocastanum	horse chestnut	72.0
Magnolia	magnolia	83.0
Aesculus glabra	Ohio buckeye	69.0
Lagerstroemia	crepe myrtle	84.0
Populus tremuloides	quaking aspen	82.0
Picea abies	Norway spruce	76.0
Pinus rigida	pitch pine	100.0
Pinus strobus	white pine	77.0
Acer truncatum	Shantung maple	80.0
Chamaecyparis thyoides	Atlantic white cedar	74.0
Carya glabra	pignut hickory	77.0
Larix laricina	American larch	80.0
Acer platanoides 'Crimson King'	crimson king maple	73.0
Picea pungens	blue spruce	83.0
Acer negundo	boxelder	72.0
Fagus sylvatica	European beech	79.0
Phellodendron amurense	Amur cork tree	66.0
Pinus	pine	85.0
Acer nigrum	black maple	77.0
Halesia diptera	two-winged silverbell	71.0
Pinus nigra	black pine	49.0
Pseudotsuga menziesii	Douglas-fir	86.0
Thuja occidentalis	arborvitae	93.0
Maclura pomifera	Osage-orange	90.0
Pinus resinosa	red pine	90.0
Cedrus deodara	Himalayan cedar	79.0
Alnus glutinosa	European alder	68.0
Tsuga canadensis	eastern hemlock	67.0
Picea	spruce	75.0
Aesculus x carnea	red horse chestnut	84.0
Cedrus atlantica	Atlas cedar	89.0
Acer buergerianum	trident maple	79.0
Chamaecyparis pisifera	false cypress	90.0
		80.0


Based ON : International Debt

3. What countries have the largest outstanding debt?


  SELECT
    cs.country_code,
    cs.region, id.country_name,id.value, id.year
  FROM
    `bigquery-public-data.world_bank_intl_debt.country_summary` cs
  
INNER JOIN 
  
    `bigquery-public-data.world_bank_intl_debt.international_debt` id
ON
  cs.country_code = id.country_code
  where cs.region!=""
ORDER BY
  id.value DESC


Output:

Row	country_code	region	country_name	value	year	
1	
IND
South Asia
India
2.42074205371E10
null
2	
IND
South Asia
India
2.42074205371E10
null
3	
IND
South Asia
India
2.42074205371E10
null
4	
IND
South Asia
India
2.42074205371E10
null
5	
IND
South Asia
India
2.42074205371E10
null
6	
IND
South Asia
India
2.42074205371E10
null
7	
IND
South Asia
India
2.42074205371E10
null
8	
IND
South Asia
India
2.42074205371E10
null
9	
IND
South Asia
India
2.42074205371E10
null
10	
IND
South Asia
India
2.42074205371E10
null
11	
IND
South Asia
India
2.42074205371E10
null
12	
IND
South Asia
India
2.42074205371E10
null
13	
IND
South Asia
India
2.42074205371E10
null
14	
IND
South Asia
India
2.42074205371E10
null
15	
IND
South Asia
India
2.42074205371E10
null
16	
IND
South Asia
India
2.42074205371E10
null
17	
IND
South Asia
India
2.42074205371E10
null
18	
IND
South Asia
India
2.42074205371E10
null
19	
IND
South Asia
India
2.42074205371E10
null
20	
IND
South Asia
India
2.42074205371E10
null
21	
IND
South Asia
India
2.42074205371E10
null
22	
IND
South Asia
India
2.42074205371E10
null
23	
IND
South Asia
India
2.42074205371E10
null
24	
IND
South Asia
India
2.42074205371E10
null
25	
IND
South Asia
India
2.42074205371E10
null
26	
IND
South Asia
India
2.42074205371E10
null
27	
IND
South Asia
India
2.42074205371E10
null
28	
IND
South Asia
India
2.42074205371E10
null
29	
IND
South Asia
India
2.42074205371E10
null
30	
IND
South Asia
India
2.42074205371E10
null
31	
IND
South Asia
India
2.42074205371E10
null
32	
IND
South Asia
India
2.42074205371E10
null
33	
IND
South Asia
India
2.42074205371E10
null
34	
IND
South Asia
India
2.42074205371E10
null
35	
IND
South Asia
India
2.42074205371E10
null
36	
IND
South Asia
India
2.42074205371E10
null
37	
IND
South Asia
India
2.42074205371E10
null
38	
IND
South Asia
India
2.42074205371E10
null
39	
IND
South Asia
India
2.42074205371E10
null
40	
IND
South Asia
India
2.42074205371E10
null
41	
IND
South Asia
India
2.42074205371E10
null
42	
IND
South Asia
India
2.42074205371E10
null
43	
IND
South Asia
India
2.42074205371E10
null
44	
IND
South Asia
India
2.42074205371E10
null
45	
IND
South Asia
India
2.42074205371E10
null
46	
IND
South Asia
India
2.42074205371E10
null
47	
IND
South Asia
India
2.42074205371E10
null
48	
IND
South Asia
India
2.42074205371E10
null
49	
IND
South Asia
India
2.42074205371E10
null
50	
IND
South Asia
India
2.42074205371E10
null
51	
IND
South Asia
India
2.42074205371E10
null
52	
IND
South Asia
India
2.42074205371E10
null
53	
IND
South Asia
India
2.42074205371E10
null
54	
IND
South Asia
India
2.42074205371E10
null
55	
IND
South Asia
India
2.42074205371E10
null
56	
IND
South Asia
India
2.42074205371E10
null
57	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
58	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
59	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
60	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
61	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
62	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
63	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
64	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
65	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
66	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
67	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
68	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
69	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
70	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
71	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
72	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
73	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
74	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
75	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
76	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
77	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
78	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
79	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
80	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
81	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
82	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
83	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
84	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
85	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
86	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
87	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
88	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
89	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
90	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
91	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
92	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
93	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
94	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
95	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
96	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
97	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
98	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
99	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null
100	
MEX
Latin America & Caribbean
Mexico
2.20718609876E10
null


Based ON: Bureau of Labor Statistics

4. What is the average annual inflation across all US Cities?

SELECT *, ROUND((100*(value-prev_year)/value), 1) rate
FROM (
  SELECT
    year, 
    LAG(value) OVER(ORDER BY year) prev_year,
    ROUND(value, 1) AS value,
    area_name
  FROM
    `bigquery-public-data.bls.cpi_u`
  WHERE
    period = "S03"
    AND item_code = "SA0"
    AND area_name = "U.S. city average"
)
ORDER BY year

Output:

year	prev_year	value	area_name	rate
1997		160.5	U.S. city average	
1998	160.5	163.0	U.S. city average	1.5
1999	163.0	166.6	U.S. city average	2.2
2000	166.6	172.2	U.S. city average	3.3
2001	172.2	177.1	U.S. city average	2.8
2002	177.1	179.9	U.S. city average	1.6
2003	179.9	184.0	U.S. city average	2.2
2004	184.0	188.9	U.S. city average	2.6
2005	188.9	195.3	U.S. city average	3.3
2006	195.3	201.6	U.S. city average	3.1
2007	201.6	207.3	U.S. city average	2.7
2008	207.342	215.3	U.S. city average	3.7
2009	215.303	214.5	U.S. city average	-0.4
2010	214.537	218.1	U.S. city average	1.6
2011	218.056	224.9	U.S. city average	3.0
2012	224.939	229.6	U.S. city average	2.0
2013	229.594	233.0	U.S. city average	1.5
2014	232.957	236.7	U.S. city average	1.6
2015	236.736	237.0	U.S. city average	0.1
2016	237.017	240.0	U.S. city average	1.2
2017	240.007	245.1	U.S. city average	2.1
2018	245.12	251.1	U.S. city average	2.4
2019	251.107	255.7	U.S. city average	1.8


5. What was the monthly unemployment rate (U3) in 2016?

SELECT
  year,
  date,
  period,
  value,
  series_title  
FROM
  `bigquery-public-data.bls.unemployment_cps`
WHERE
  series_id = "LNS14000000"
  AND year = 2016
ORDER BY date

Output:

year	date	period	value	series_title
2016	2016-01-01	M01	4.9	(Seas) Unemployment Rate
2016	2016-02-01	M02	4.9	(Seas) Unemployment Rate
2016	2016-03-01	M03	5.0	(Seas) Unemployment Rate
2016	2016-04-01	M04	5.0	(Seas) Unemployment Rate
2016	2016-05-01	M05	4.8	(Seas) Unemployment Rate
2016	2016-06-01	M06	4.9	(Seas) Unemployment Rate
2016	2016-07-01	M07	4.8	(Seas) Unemployment Rate
2016	2016-08-01	M08	4.9	(Seas) Unemployment Rate
2016	2016-09-01	M09	5.0	(Seas) Unemployment Rate
2016	2016-10-01	M10	4.9	(Seas) Unemployment Rate
2016	2016-11-01	M11	4.7	(Seas) Unemployment Rate
2016	2016-12-01	M12	4.7	(Seas) Unemployment Rate


6. What are the top 10 hourly-waged types of work in Pittsburgh, PA for 2016?
SELECT
  year,
  period,
  value,
  series_title
    
FROM
  `bigquery-public-data.bls.wm`
WHERE
  series_title LIKE '%Pittsburgh, PA%'
  AND year = 2016
ORDER BY
  value DESC
LIMIT
  10

Output:



Based ON: Google Analytics Sample
7. What is the average number of transactions per purchaser?

  SELECT
    fullVisitorId,
    SUM (totals.transactions) AS total_transactions_per_user
  FROM
    `bigquery-public-data.google_analytics_sample.ga_sessions_*`
  WHERE
    _TABLE_SUFFIX BETWEEN '20170701'
    AND '20170731'
    AND totals.transactions IS NOT NULL
  GROUP BY
    fullVisitorId 

Output:

fullVisitorId	total_transactions_per_user
0862593861789084986	1
3346631104336405882	2
1647919038367422597	1
1470956649294061383	1
1383687428379664179	1
2817453656935743519	1
9824524325763367768	1
7183166419038940327	1
3551066677390608620	1
1210036509049986390	1
1842106171508051051	1
0112712853580593351	1
0507664246019057034	1
8303950448649190197	1
235352179583924900	1
7454160401328902482	1
6817073554026572260	1
9541996968314639199	1
6861967258484656845	1
616813475440297008	1
8903811163323410238	1
6397329721784535287	1
9680451704023510043	1
410236987316567002	1
2034812653909210223	1
5292294760335216459	2
186231215995844689	1
0345672699449577691	1
5258378690008715588	1
2703137619338184529	1
4680625557979147601	1
4408662176448539530	1
9598871851189945502	3
1681975491896946073	1
6686381334657841223	1
9445171435422230535	1
9687976620185337812	1
7455554400123317161	1
7188768914363923661	1
473905218555423969	1
0389488682405584834	1
7745913892709272663	2
0047078955120420928	1
1190814633327628141	1
7284107994229493297	1
4064135835973062555	1
314623674794258357	1
2144335436738770147	1
813207140579582070	1
527426783375720325	1
8572246047047081810	1
0842088345978971117	1
2981325201816358942	1
3156558389889250659	1
238925310298938861	1
7483600664917507409	1
8619176562727195197	1
8718443071348965186	1
4735021838862063499	1
6513685604083648974	1
2837725284997269762	1
8698140093733128307	1
163910434575936100	1
6110519761832647760	1
3700543276431412713	1
0128830210468179660	1
8780445498294202074	1
9475000972333610150	1
5853503812958964619	1
5001293816565919651	2
5584411114546174652	5
1656927552400476520	1
0531829155524217247	1
4531918958295106898	1
0097563825178820508	1
7517029078565627714	1
2610708601231231422	1
972856631604465767	1
6189137290295727859	1
5976867149100083641	1
4795790370118359645	1
5975789416845370133	1
5369585818624352954	1
1442612237985610717	1
6005829572969771144	1
8180992226439641389	1
0456807427403774085	1
2024172620398136134	1
3641847080616677863	1
9007057960603042466	1
9890182105631590481	1
948321323323223626	1
6775926571390989746	1
6171698148494823293	1
7782965489086957079	2
1575299870459163170	1
6185798445433721880	1
1476938238176225678	3
1703470801983285779	1
983622469844382741	1
8250431010473509037	1
5224330515080725566	1
9556550673068144771	1
8966349442774967540	1
7248845288199471059	1
9302767552528832368	1
9336440504907193236	1
3736964846520654455	1
8977039158734679466	1
5774321029448220916	1
0608915197735218105	2
7111968133200925943	1
9905174730865679854	3
217143916288493658	1
2616271879571385041	1
9673964860189487919	1
2969418676126258798	1
6873140036612855431	1
1675171647898452800	2
2118556556010692812	1
5772921781547143127	2
7406115845826379585	1
481908738776854721	1
599110551792149234	3
7974747290395913881	1
3139557393320178005	1
9060309108953686961	1
0696402585067597025	1
4988517937139937145	1
1392760476578326953	1
2689556653800639103	1
9972641923092309898	1
9179364299608933418	1
8669188840409334896	1
4370296679036736835	1
5239443997664471780	1
7409212089173005419	1
3971437232101672363	1
4545152794461452964	1
9954291757269899812	1
7105031024714443566	1
6644273643966013405	1
6390628371128313999	1
6373394558572820546	1
4570976451995896965	1
5960127137243713650	2
4327496999674034617	1
0779199793341944056	1
2158257269735455737	3
3680244960768233462	2
2966611128426241872	1
1288317908843556558	1
6152978475187911748	2
1447257816279888170	1
3830485242574967009	1
2797925470043622325	1
4284747478619287722	2
9166972626679050152	1
6987303552830349046	1
7633475394444208361	1
9278147896530416985	1
1973770164859106217	1
6332990203478940744	1
7466690540565937255	1
3471594580435227032	1
990017562279683512	1
1713847086511016991	1
9095973446989997244	1
8912902059525758308	1
4615467220494146394	1
5587285412268223147	1
5671688466209278718	1
8151349247637576196	2
3053417453950406791	1
5735858296023788680	1
6297544198548387157	2
6236695646664370912	1
1152695544079009829	1
5763555354582854124	1
9654518257837426461	1
4921798700570421930	1
165109760635455356	1
3273268557987890623	2
4140153693332318188	1
9598226286194728257	1
7933171750259720017	1
1931486566224793189	1
9530536315613357862	3
7238649130733042064	1
1452613891025216774	1
7395718173947720444	1
5402622110310553851	1
4376572204985925602	2
2366243354794689639	1
0169854884741652554	1
854434256389492978	1
2533769468325451038	1
9076419614508247108	1
2348681849763325965	1
7282058185499112847	2
6448510043360208590	1
96843987855909025	1
3538189268879245816	1
3140693833607536032	1
5481081028229796179	1
2872390777688988558	1
7559458489771407786	1
302704045753662604	1
5369128368163820088	1
1063109698143249629	1
2888994662401288163	1
4871978976437661341	1
3027900979672030556	1
3012297793847553299	1
6198200760309203581	1
7285581814755922222	1
8718769444040470230	1
6414469815060591671	1
2105122376016897629	1
3768290334696236505	1
0396718069117936487	1
057693500927581077	1
0658019277799848735	1
0193361951439999580	1
5700698092270325485	1
3575773830913742237	1
5691228855195017010	1
719763844495200108	1
4858273376881706416	1
5540724306740925009	1
702564824793049879	1
1025574386832469970	1
067475292701707948	1
7507699100891959218	1
6051908919929899878	1
7911961580493101960	1
5095160033645238155	1
491177567878140069	1
544222846238969798	1
1693439860882386132	1
1677668617700674850	1
8972388387130785286	1
7451284399359627657	1
2637714150350706913	1
5639438910924480453	1
0363878417378060116	1
3912300160509220549	1
4230960861530232531	1
6400178996598013044	1
3822207688294082684	1
9868557064314705324	1
8676763420791275254	1
1216838692754057393	1
4717136695286769796	1
6081065027477521968	1
2308631730639284715	1
875410720669459903	1
4241769030360346425	1
6465870836529202272	1
3978330627656387084	1
8009185599443907717	1
0951967559171152344	1
1051896220301954151	1
5816514381907176001	1
3023987141192180181	1
7741904137426649634	1
2439011587487738686	1
4558105233287956143	1
9711893424833628957	1
1751309915031023278	1
3424918216070852195	1
0604314853571328266	1
5248418277725722133	1
8657427332734176422	1
1761084588077503545	1
3854579461029873656	1
3210357805056492900	1
6752966524308578195	1
1166095149523935137	1
0367699875055542808	1
454845221896711463	1
7736543262187152126	1
623238387362841295	1
0975931442450346746	1
5365708442015077167	1
0640040708763897460	1
1875268638592946287	1
83055806370747628	1
0500460722094613747	1
3551040750443861038	1
6274615038428740035	1
6646523251391378796	1
0080479763428955064	1
7797161228996458724	1
160370198171303042	1
7880178108492772399	1
9460311742865907976	1
8197879643797712877	1
2551061282285178751	1
7447137895250670218	1
9505484401754648749	2
8744897619448167360	1
1665687379365770562	1
2557544565676711160	1
2084416927014276438	1
884821390104728104	1
1790630358090197146	1
9026840718082010040	2
5437013238128269518	1
4019468962441063327	1
1465921528988606892	1
7588981130462792361	1
0647701940544723891	1
682549734570999775	1
2618807484848182971	1
7985347873719599013	1
4702607995709465702	1
2075444661051129697	1
4377378313866337368	1
859169837119660000	1
339334311045885434	1
9363207205094761073	1
3550517741801560701	1
4577377706293036618	1
9249130983722228273	2
6125563692107396483	1
8010758488625619131	1
543368443296403226	1
644407009401848542	1
7567817112637547239	4
9587233052829072755	2
262902792123089700	1
2966465528641096132	1
036131108463384213	1
2122547835443026286	1
69932627935135372	1
5980795059692822710	1
7109365960506850158	1
4381707062146143113	2
806992249032686650	3
3658549305813344156	1
3296760629290615445	1
4062630166370650304	1
7445235885559107095	1
8321566838784998459	1
4218367025544931420	1
4952396078130707023	1
442359446750687328	1
1573919593896895308	1
0280589015308186459	1
7463172420271311409	1
6494204056900967959	1
5922545727078253740	1
9433517997046669782	1
7183243391284715656	1
7232030663207265797	1
8261368202596858055	1
2687747268928070384	1
1785770568670204175	1
7478106734160303595	1
4656286722064696063	1
3221924345288041502	1
135731445166621856	1
0893919105830368772	1
3972481072101395162	1
8636734210084365159	1
6361004934465135812	1
1342741603893289943	1
682241557361742402	1
5286653810282194817	1
6822029585974279558	1
6979205517954044794	1
2440774884535248016	1
4938796308846198678	1
9213584705844626996	1
8040137666683755877	1
0663614479606200802	1
5823529938186171963	1
2352548628524812063	1
2364782563241908647	1
4154041461958944095	1
0294093638755103061	1
525470181967108180	1
2624131748689653933	1
107029174520648874	1
1338601940113408411	1
4855673784399652593	1
4833825011669343831	1
1973279275238171732	1
049618887282998852	1
4871826258834761103	1
8923902094377758912	1
5097087346105463693	1
1722480716347032461	1
6302382540936873657	1
5112369122544987822	2
3784608915391176306	1
7166449056011989823	1
4175693739550513271	1
5232863160454746212	1
8899113493615355633	1
0318476411656972479	1
856273082667959194	1
8825602309761363794	2
4540509568993725359	1
240359488343865855	1
6373565169411439679	1
3036945143044651672	1
0702289726935404752	1
085319952392271706	1
9832163989743197601	1
9879056257140317872	1
5590346028970118637	1
9911451154506607743	1
1255368394012652243	2
7320316463607490470	1
9740627261104812573	1
6390036557697403871	1
1160204963389257110	1
9089896742439819665	1
3700714855829972615	2
4693422077502534585	1
1922510765164338251	1
2219981041933608843	1
4683498388367209057	1
7824102392765552707	1
0326671467950015369	1
4624790961997446284	1
1468478016521432136	1
8836497360273825933	1
5546793669751235607	1
6014980722805375499	1
9519825248461982188	1
3563510904717248245	1
8122366843389255502	1
3308953517897542519	1
8624185886173345427	1
9001502916626110125	1
6312194749319574796	1
9602459823241782836	1
6246146960091353412	2
4984366501121503466	1
1424707127501880055	1
6974476474190004026	1
8804905634731085002	1
5657677988182303423	1
8220211701749350854	1
4626256438410154733	1
5538435101700540876	1
8525552808729629890	1
4902563928132780662	1
3179916194458138070	1
5185882727774791811	1
4034510370290015321	1
6443595642175123029	1
6053317410808350071	1
1424355572088327868	1
963845761761571092	1
1182675562893088634	1
2141032560407740130	1
0548744394505098293	1
0652202420147185334	1
8277644417832306861	1
2491238829943520906	1
452384137560800015	1
3454415788904146693	1
8528973034561269758	1
689318192161645703	2
1563065767696461622	1
7115815619589342932	1
6052206455243513477	2
6366523937097011266	1
6568405082195988335	1
0743501820485430157	2
2572686632526205558	1
7125068043444176386	1
4071592194862232855	1
4074582003417698725	1
6586739058236606680	1
2224572703195879390	2
2494927659578259711	1
606735064258270722	1
4260968995177655855	5
0316080058721038988	1
4613547766859466698	1
5021888768610000663	1
4574431826625163321	1
9509348681300444250	2
7194598190853071809	1
3708624609955414339	2
7169974092956652971	1
8579647481420425960	1
444821471625212420	1
1999942187402858600	1
597489337358394308	2
0668741043882663600	1
1413421667450087159	1
4299030824455740972	2
4073209630928256180	1
5614933090112217012	1
2779594039917451826	1
336251173702144221	1
6140447030610096925	1
6026865008041115729	1
4602383891226401804	1
5328385563084211127	1
0024932550342595467	2
9512976956663565169	1
7181128763936845788	1
6623534661206058922	1
081281456829886913	1
1383949428914741700	1
9745349280610704454	1
7704158452522194564	1
8910769516525628891	1
8838657285552913253	1
354395446181773550	1
2584510701660360932	1
9802926311803722380	1
9856403899995722473	1
0967510812862831126	1
0774683549194942679	1
261669143599587910	1
5812572929202367937	1
8901669251595592717	1
4068647851581953751	1
9448751983627817237	1
1947343681843355858	1
4339064982507273483	1
425433276966204823	1
8836653961966700632	1
9707913144913687378	1
8519577869545508855	1
5670613208439164608	1
6502669189284720026	1
749967699578346374	1
4178948793864037103	4
5923041114491111329	1
2256968435490294758	1
3931961473816782577	1
3916248033880457849	1
8076506950151787875	1
947193476266502800	1
8737287377964426748	1
9495542473910378037	1
7824759881998320555	1
4026449406503874324	1
9119794344298537076	1
889422988902631033	1
8430163495777040605	1
819296301112227931	1
8573628711430738315	1
1459050472203168026	1
7054256782754973251	1
1868405397995157975	1
2527677375017653674	1
7372141474604813858	1
8821726080717309200	1
109375183949292344	1
306293428725549657	1
3028560396160352119	1
0372741889888882659	1
9104296808650483352	1
7757589561918883331	1
873320659256976904	1
8540688286241364465	1
3004433257206076818	1
8239546374178075911	1
3898563466459211162	1
15618322761092379	1
1727715375435944327	1
2422865366235727605	1
9104901150360487546	1
3968161907727043413	1
4274511861314211339	1
6310913035223827948	1
4119448635627172848	1
6800222720402902812	1
6704364789762409859	1
9519477824585169413	1
733935141047180090	1
395878510909861453	1
5296297372596099151	1
7866268239897048336	2
8915655068975271461	1
8639551625314218823	1
2266837403735683845	1
6642261851584081073	1
8421245050853915723	1
2287406421504796570	1
2249724102559347990	1
8308144532481482080	1
3743916662879082495	1
7701571111733834937	1
4410953563194536742	1
8382560140451028355	1
4883249725302903151	1
5962830800899970265	1
9613834008182881588	1
2049749565428127211	1
7846265776310082337	1
5256372508003021503	1
1958192249642375634	1
3490620713275982342	1
4827442520440231767	1
4013470531611520402	1
7401384748988164586	1
2638377830326163737	1
3747999856310382299	1
8021812938751479108	1
2178459566193458788	1
4045831322438555082	1
2590088265600782267	1
0953889584295924240	1
4640309372934566564	1
8154318582372771955	1
6204463650092781278	1
1193832537421178696	1
7481522828290694645	1
051516119104547275	1
5552453019078254306	1
8287454401511660857	1
8810145279946425641	1
1205098047899006231	2
4957622252319100547	1
9947665738712650436	1
2923157586809674604	1
478403815632492375	1
4068416534578096540	1
263896833266166939	1
2818796658906330904	1
4242693912596237127	1
6605741812021030281	1
3300270774997102814	1
8259756799557639912	1
2017396058039056855	1
3558104655978527434	1
4587210925935196615	1
2868753573471668678	1
2728484397720314035	1
5470058724579220258	1
1090774782213816251	1
594511863093043281	1
4773573244753299893	1
0546450430035162938	1
0572135527461851083	1
5991536664355896877	1
3123912150867532904	1
7303461177926085857	1
0312226371899637611	1
0142116411233847758	1
5155886278275887447	1
2396255136764683002	1
3741029495705540856	1
9484234336257707179	1
9014580000597240539	1
5753687412615654863	2
7308330363798605080	1
5807278314451544984	1
6361412319872992079	1
6560066529199965530	1
403789659645595849	1
3891707253957252733	1
9376652341885109410	1
5615435557331654733	1
120951074287268149	2
7701613595320832147	3
0509537543362594682	1
9417857471295131045	9
5451348672261739783	1
8149979272084433494	1
7637038443893798015	1
6238089889459333091	1
1921325710867532207	1
7227604725376239031	1
387849079599046538	1
4030851960983791121	1
4950411203281265700	1
8530723892127582602	1
4688218153840595469	1
5687667730920600613	1
0010295111715775250	1
6684428411656994293	1
9227772112500941696	1
8064625150033508396	1
5139927098906360724	1
7979010430069561046	1
2766162501835274072	1
9398183614127015265	1
2863616485775419102	2
2426971819031028277	1
4845279744517849233	1
9849207490494234255	1
0214776722271775969	1
6245962080386953755	1
9784853758319873850	2
9974351919673138742	1
9746124619174084370	1
3945002194355797350	1
039400440658825933	1
1280993661204347450	2
8133234491242505022	1
5402571042001627330	2
5355878105237295955	1
1152177248793735167	1
6215579195601546611	1
9858575902161625282	1
0972673302515080474	1
6338909403180350961	1
3061154222126395175	1
6335554848851534266	1
953713676730854570	2
6803256328892941875	2
5441957633456467994	1
947967641100341579	1
22078954710203778	1
0376394056092189113	3
1804930412747691262	1
703628343876693893	1
4958103240836842867	1
6526089365203867148	1
0014262055593378383	3
1501922563642798112	1
7211075105637086382	1
0236160742740831906	1
2729326042885052223	1
16925875208939543	1
6483542972874741074	1
4376369621294658596	1
6432310188343340425	1
5564329510174099370	1
6075418837768242958	1
4462569127423521108	1
7213484590531142958	1
0679581364401887394	1
8194948038979976753	1
3053164528707250163	1
3452520076908363504	1
9431575744211678902	1
1459360539535171755	1
9521438372294298977	1
587886297354228717	1
9737166459620980047	1
9374732127201012465	1
5215840735346366486	4
0097371986665596420	1
0349598333236458498	1
2155115683587711916	1
4920953157538129017	1
1005326553546138067	1
1053771337658446740	1
5199370466032130686	1
9240425877262756231	4
3303034042373276972	1
1459959210477445011	1
0853682097133967435	1
6827945352712857729	1
190492934318255272	1
9629138648067304387	1
47511660497565285	2
3533141636411834269	1
4978615078876520186	1
4042880551685271731	2
7089296120636038584	1
1863054289029276927	1
9422085418164335542	1
9035173114644245964	1
5000038412644544234	1
2812654087924931640	1
372706149688864468	1
6736977205570964943	1
1393633173328801040	1
2459432206617896206	1
3948753572772915413	1
7012131705583674177	2
1741172694620038876	1
7404717158530100525	1
9677097503012171995	1
8005996482635469170	1
449424538549488734	1
9219609257103359166	1
1174647913878447921	1
5135901390896357467	2
3004593292265626624	1
391734717153151205	1
5063074873295543663	1
9963197880398595287	1
3058457482106046803	1
7954367393399826900	2
5342879446684210628	1
4105754576329014219	1
2314697698664321051	1
4708133624098231997	1
0795389678082168807	1
2338178303528914061	1
7731162068091223593	1
6968323948324124881	1
3156235512146749592	2
1675608109098320028	1
1164110348121511511	1
7803437096506812413	1
0082806901961150595	1
5656797100186681238	1
9102474086699884011	1
2271817805906914184	1
9263852900501117129	1
5125140299363465569	1
2367296881084974931	1
9293223521534878892	1
1762540039573649288	1
5006795078292798707	1
8478498564954638951	1
1835132804289989526	2
344338099914658416	1
8800304863528971642	1
195434588004709231	1
3131378609982399583	1
2134229956335427014	1
2377126524987232945	1
4901167500019826035	1
3702504149982325265	1
9199984406158134288	1
446821635919209531	1
0249659095832018179	1
6885840890081039756	1
7487437966424965141	1
1311682260438379600	1
6997260560132631354	1
9926655339980503224	1
2979158334748499173	1
1140574847502258865	1
9973665079624172058	1
7650573166348333190	1
0143782636543876435	1
157019484210987302	1
330070454475724462	1
3927815032450931689	1
7724099657846251773	1
4552275222012095884	1
9583683554162057560	1
3865564441178018664	1
4589600625729389981	1
670722016498267	1
3839596841653772572	1
43770390702768717	1
7910024669087314685	1
3295470093238310609	1
0429502726115959763	1
0183218035021860438	1
5694129009662162026	1
0633547848089854806	1
746147040518715564	1
7853124250162225215	1
4143932736586919766	2
0884726487864103521	1
0878293552935562825	1
3954784642722657723	1
2929956217778331899	1
0006911334202687206	1
4332781117641254031	1
9654758935896158776	1
42872006688710090	1
6234607912924259841	1
7859759557446158559	1
8305324219354284523	1
8719867302995619824	1
7591955684159608805	1
1774472718303082739	1
9391607314160932483	1
4895430552956512702	1
713731982901764318	2
557267724728292293	1
2199373686188473715	1
1673188218512892503	1
4981679382824177253	1
0794644147217997845	1
7063315126654210750	1
7783483124481840961	1
5185645869012304658	1
5612807768965191337	1
2302897932992284309	1
7303793848128238288	1
1766574900434071803	1
7547701694662050330	1
0747495245317338179	1
950676259034422019	1
5714578235466782917	1
9469111554165256569	1
4737716055104076300	1
2433182968898386515	1
4136548162519732667	1
0344842538233543056	1
2341448488539470965	1
1996186587769697436	1
0163532416839889055	2
4572473880059546924	1
0600237702497948707	1
2522954230696043073	1
6752104622110349075	1
0640433429877929929	1
7771380615067157220	1
3092487309701391768	1
3310309019453934499	1
8375075536798804409	1
9846963060470956023	1
397440133393463294	1
5840295243911523760	1
4807930160918189094	1
1247282406356396417	1
4140559214164857738	2
4146222468180363567	2
0780253600713375371	1
0763707560320645222	1
169337349809177349	1
6284948773679645206	1
5039693679894183284	1
3680806121011427493	1
2438001988287339845	1
2736979716085988579	1
2645557375569096181	1
4352760646905266733	2
0535797652559788641	1
7171943038143298955	1
1081954083914922307	1
3813195472927677467	1
5322397769480961983	1
8230689683989624083	1
1958518504412290611	1
5066382323992610838	1
8930278305459563871	1
7730778110265788269	1
6486795623038216247	1
330062846836232829	1
3117505679893009709	1
9305224849656676534	1
1712066703099487652	1
746996333765865062	1
3694234028523165868	1
2760610370970936430	1
5569275433551045400	1
9344315745283537381	1
3117858606721790013	1
6939779416249682537	1
0088657980877164102	1
5367424131768491778	1
3302292601270378852	1
704373157724192220	1
7999804494517330141	1
2163555648381499404	1
8151988731272450660	1
5056841379210378275	1
2354405029601095288	1
2264010855758956307	1
6325377874048923314	1
5508164318239659326	1
0405996727678488611	1
1929978424426570223	1
8671741245048754342	2
3724383329494779540	1
8364082612050395902	1
4787370740481074044	1
0956108016718766611	1
1931723981901564088	1
5952422370450576468	1


8. What is the total number of transactions generated per device browser?

SELECT
  device.browser,
  SUM ( totals.transactions ) AS total_transactions
FROM
  `bigquery-public-data.google_analytics_sample.ga_sessions_*`
WHERE
  _TABLE_SUFFIX BETWEEN '20170701'
  AND '20170731'
GROUP BY
  device.browser
ORDER BY
  total_transactions DESC

browser	total_transactions
Chrome	984
Safari	65
Firefox	12
Internet Explorer	7
Opera	2
Edge	2
Opera Mini	
UC Browser	
Safari (in-app)	
Mozilla Compatible Agent	
YaBrowser	
Seznam	
MRCHROME	
SeaMonkey	
Iron	
Android Runtime	
Mozilla	
Coc Coc	
Android Browser	
Maxthon	
Amazon Silk	
Nintendo Browser	
0	
(not set)	
Android Webview	
Puffin	
BlackBerry	
[Use default User-agent string] LIVRENPOCHE	
osee2unifiedRelease	


Based ON : SEC Public Dataset

9. Total company revenue per state in the USA
SELECT
  Submission.state AS state,
  SUM(QuickSummary.revenue) / 1e9 AS revenue_per_state_in_billions
FROM (
  SELECT
    submission_number,
    MAX(value) AS revenue
  FROM `bigquery-public-data.sec_quarterly_financials.quick_summary`
  WHERE
    measure_tag IN ('Revenues', 'SalesRevenueNet',
                    'SalesRevenueGoodsNet')
    AND fiscal_year = 2016
    AND fiscal_period_focus = 'FY'
    AND number_of_quarters = 4
  GROUP BY
    submission_number) QuickSummary
 INNER JOIN (
   SELECT
     submission_number,
     MAX(stprba) AS state
   FROM
     `bigquery-public-data.sec_quarterly_financials.submission`
   WHERE
     stprba IS NOT NULL
     AND stprba != ''
     AND countryba = 'US'
   GROUP BY
     submission_number) Submission
 ON
   QuickSummary.submission_number = Submission.submission_number
GROUP BY
  state
ORDER BY
  revenue_per_state_in_billions DESC;

Output:

state	revenue_per_state_in_billions
TX	2300.915654691
CA	1858.172731464
NY	1768.027321482
IL	912.302021649
OH	683.309693325
MN	667.00903881
WA	630.67086953
MI	593.837801663
AR	572.769187331
PA	525.456289241
GA	476.463322285
NJ	473.014949089
MA	404.195367001
FL	369.117817901
CT	363.795442461
VA	360.389792041
MO	342.732442637
NC	332.854869434
NE	270.611244363
TN	221.928920871
CO	211.126498256
RI	211.021730853
IN	199.601885878
OK	160.502671999
WI	156.684489383
KY	134.697804821
AZ	122.036979375
MD	114.705609698
NV	74.703914282
DE	71.730690032
KS	64.358005011
IA	62.904496246
OR	53.650418644
ID	39.160909879
LA	34.168351101
AL	30.27158358
UT	30.046485879
DC	25.831454
SC	21.433035674
NH	11.701474
HI	8.649620458
ND	6.952088398
MS	4.979659069
SD	4.766926083
ME	2.838952083
AK	2.271931
WY	1.3241625
VT	0.692984687
WV	0.15950356
MT	0.103111739
NM	0.005523694


Based ON : US Roads

10. How many unique roads are in New York City?
SELECT
  COUNT(DISTINCT(road_id)) AS nyc_road_count
FROM
  `bigquery-public-data.geo_us_roads.us_national_roads` r inner join 
  `bigquery-public-data.geo_us_census_places.us_national_places` p
ON
   ST_WITHIN(road_geom, place_geom)
  AND name_lsad LIKE "%New York city%"
  AND p.state_name = "New York"
  AND r.state_name = "New York"

Output:

nyc_road_count
22064
