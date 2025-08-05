# Dataset_G10
Se eligió el dataset: Crimes against women in India from 2001 to 2021 (https://www.kaggle.com/datasets/balajivaraprasad/crimes-against-women-in-india-2001-2021?resource=download), por las siguientes características:
1. Aunque el dataset se centra en crímenes en general, puede haber casos de ciberdelincuencia incluidos.
2. Al analizar los datos de crímenes en India asociado a mujeres, podríamos identificar patrones y tendencias que son útiles para prevenir futuros crímenes.
3. La delincuencia es un problema importante en muchos países, incluyendo India. Al analizar los datos de crímenes, podríamos contribuir a mejorar la seguridad nacional y la seguridad de los ciudadanos.
4. Un dataset sobre crímenes en India podría ser un buen ejemplo para aplicar técnicas de machine learning, como la clasificación y la regresión, para predecir patrones y tendencias en la delincuencia.
Los objetivos fueron 
- Analizar los patrones y tendencias en los crímenes en India.
- Identificar las características más importantes que contribuyen a la delincuencia en India y su relación con la obtención de datos relevantes.
Explicación de los pasos de limpieza y transformación
Se identificó que el dataset tenía datos basura los cuales no aportaban al análisis.
Se verifico la calidad de los datos buscando errores, valores en blanco o inconsistencias.
Se identificó inconsistencia en el nombre de las regiones, con valores repetidos entre mayúsculas y minúsculas, se estandarizo los nombres de las regiones con:
df['State'] = df['State'].str.upper()
df_standardized = df.groupby('State')[['Rape', 'K&A', 'DD', 'AoW', 'AoM', 'DV', 'WT']].sum().reset_index()
display(df_standardized.head())
 
En el año 2011 no se tenía un valor para el “Asalto contra mujeres por año”, por lo que se colocó un promedio entre el año 2010 y 2012, con el siguiente código
Principales hallazgos del análisis
aow_2010 = asalto[asalto['Year'] == 2010]['AoW'].iloc[0]
aow_2012 = asalto[asalto['Year'] == 2012]['AoW'].iloc[0]
promedio_aow = (aow_2010 + aow_2012) / 2
 
- Incremento de muertes y violaciones: estos resultados sugieren un aumento en la frecuencia o gravedad de estos crímenes, lo que podría ser un indicador de una situación de seguridad preocupante en la región del año 2001 al 2021