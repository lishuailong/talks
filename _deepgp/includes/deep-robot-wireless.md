\ifndef{deepRobotWireless}
\define{deepRobotWireless}
\editme

\include{_gp/includes/robot-wireless-gp.md}
\include{_deepgp/includes/deepgp-enhance.md}

\code{layers = [y.shape[1], 10, 5, 2, 2, x.shape[1]]
inits = ['PCA']*(len(layers)-1)
kernels = []
for i in layers[1:]:
    kernels += [GPy.kern.RBF(i, ARD=True)]}
	
\code{m = deepgp.DeepGP(layers,Y=y, X=x, inits=inits, 
                  kernels=kernels,
                  num_inducing=50, back_constraint=False)
m.initialize()}

\code{m.staged_optimize(messages=(True,True,True))}

\displaycode{fig, ax=plt.subplots(figsize=plot.big_wide_figsize)
plot.model_output(m, output_dim=output_dim, scale=scale, offset=offset, ax=ax, 
                  xlabel='time', ylabel='signal strength', fontsize=20, portion=0.5)
ax.set_ylim(ylim)
ax.set_xlim(xlim)
mlai.write_figure(figure=fig, filename='../slides/diagrams/deepgp/robot-wireless-deep-gp-dim-' + str(output_dim)+ '.svg', 
                  transparent=True, frameon=True)}
				  
\subsection{Robot WiFi Data Deep GP}

\includesvg{../slides/diagrams/deepgp/robot-wireless-deep-gp-dim-1.svg}

\displaycode{fig, ax=plt.subplots(figsize=plot.big_wide_figsize)
plot.model_sample(m, output_dim=output_dim, scale=scale, offset=offset, samps=10, ax=ax,
                  xlabel='time', ylabel='signal strength', fontsize=20, portion=0.5)
ax.set_ylim(ylim)
ax.set_xlim(xlim)
mlai.write_figure(figure=fig, filename='../slides/diagrams/deepgp/robot-wireless-deep-gp-samples-dim-' + str(output_dim)+ '.svg', 
                  transparent=True, frameon=True)}

\subsection{Robot WiFi Data Deep GP}

\includesvg{../slides/diagrams/deepgp/robot-wireless-deep-gp-samples-dim-1.svg}

\subsection{Robot WiFi Data Latent Space}

\includesvg{../slides/diagrams/deepgp/robot-wireless-ground-truth.svg}

\displaycode{fig, ax = plt.subplots(figsize=plot.big_figsize)
ax.plot(m.layers[-2].latent_space.mean[:, 0], 
        m.layers[-2].latent_space.mean[:, 1], 
        'r.-', markersize=5)

ax.set_xlabel('latent dimension 1', fontsize=20)
ax.set_ylabel('latent dimension 2', fontsize=20)

mlai.write_figure(figure=fig, filename='../slides/diagrams/deepgp/robot-wireless-latent-space.svg', 
            transparent=True, frameon=True)}
			
\includesvg{../slides/diagrams/deepgp/robot-wireless-latent-space.svg}


\endif
