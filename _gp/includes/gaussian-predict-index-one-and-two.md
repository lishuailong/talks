\ifndef{gaussianPredictIndexOneAndTwo}
\define{gaussianPredictIndexOneAndTwo}
\editme

\setupdisplaycode{import pods
from ipywidgets import IntSlider}
\displaycode{pods.notebook.display_plots('two_point_sample{sample:0>3}.svg', '../slides/diagrams/gp', sample=IntSlider(9, 9, 12, 1))}

\newslide{Prediction of $\mappingFunction_{2}$ from $\mappingFunction_{1}$}

\slides{
\startanimation{two_point_sample2}{9}{12}
\newframe{\includesvg{../slides/diagrams/gp/two_point_sample009.svg}}{two_point_sample2}
\newframe{\includesvg{../slides/diagrams/gp/two_point_sample010.svg}}{two_point_sample2}
\newframe{\includesvg{../slides/diagrams/gp/two_point_sample011.svg}}{two_point_sample2}
\newframe{\includesvg{../slides/diagrams/gp/two_point_sample012.svg}}{two_point_sample2}
\endanimation
}

\notesfigure{\includesvg{../slides/diagrams/gp/two_point_sample012.svg}{}}
\notes{\caption{The joint Gaussian over $\mappingFunction_1$ and $\mappingFunction_2$ along with the conditional distribution of $\mappingFunction_2$ given $\mappingFunction_1$}}
\endif
