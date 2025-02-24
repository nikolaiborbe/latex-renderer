<script lang="ts">
	// No extra logic needed.
</script>

<h1 class="mt-20 text-2xl font-bold">LaTeX Cheat Sheet</h1>

<!-- A responsive grid that becomes 1 column on small screens, 2 on medium, 3 on large -->
<div class="grid grid-cols-1 gap-10 pt-10 md:grid-cols-2 lg:grid-cols-3 ">

	<!-- Font Face -->
	<div class="w-full">
		<h2 class="mb-2 text-xl font-semibold">Font Face</h2>
		<pre class=" p-4">
\textrm&#123;text&#125;
\textit&#123;text&#125;
\textbf&#123;text&#125;
\texttt&#123;text&#125;
\textsc&#123;text&#125;
\textsf&#123;text&#125;
\textsl&#123;text&#125;
\emph&#123;text&#125;
    </pre>

		<h3 class="mb-2 font-semibold">Font Size</h3>
		<pre class=" p-4">
\tiny, \scriptsize, \footnotesize
\small, \normalsize, \large,
\Large, \LARGE, \huge, \Huge
    </pre>
	</div>

	<!-- Math-mode Symbols -->
	<div class="w-full">
		<h2 class="mb-2 text-xl font-semibold">Math-mode Symbols</h2>
		<pre class=" p-4">
\leq, \geq, \neq
\approx, \sim, \simeq
\in, \notin
\subset, \subseteq
\cup, \cap
\land, \lor, \lnot
\forall, \exists
    </pre>

		<h3 class="mb-2 font-semibold">Delimiters</h3>
		<pre class=" p-4">
( ), [ ], \&#123; \&#125;, \langle \rangle
\left( \right), \left[ \right]
\left\&#123; \right\}, \left. \right.
    </pre>
	</div>

	<!-- Greek Letters & Math Alphabets -->
	<div class="w-full">
		<h2 class="mb-2 text-xl font-semibold">Greek Letters &amp; Alphabets</h2>
		<pre class="p-4">
\alpha, \beta, \gamma, \Gamma
\delta, \epsilon, \zeta, \eta
\theta, \Theta, \lambda, \Lambda
\mu, \nu, \xi, \Xi
\pi, \Pi, \rho, \sigma, \Sigma
\tau, \phi, \Phi, \psi, \Psi
\omega, \Omega
    </pre>

		<h3 class="mb-2 font-semibold">Math Alphabets</h3>
		<pre class="p-4">
\mathbf&#123;v&#125;
\mathbb&#123;R&#125;
\mathcal&#123;L&#125;
\mathfrak&#123;g&#125;
    </pre>
	</div>

	<!-- Accents & Common Operators -->
	<div class="w-full">
		<h2 class="mb-2 text-xl font-semibold">Accents</h2>
		<pre class="p-4">
\hat&#123;x&#125;, \bar&#123;x&#125;, 
\vec&#123;x&#125;, \dot&#123;x&#125;
\ddot&#123;x&#125;, \tilde&#123;x&#125;,
\widetilde&#123;xyz&#125;
    </pre>

		<h3 class="mb-2 font-semibold">Common Operators</h3>
		<pre class="p-4">
\sin, \cos, \tan, \arcsin
\arccos, \arctan
\ln, \log, \exp
\lim, \max, \min, \sup, \inf
\sum_&#123;i=1&#125;^&#123;n&#125;, \prod_&#123;i=1&#125;^&#123;n&#125;
\int_&#123;a&#125;^&#123;b&#125;, \oint, \partial
    </pre>
	</div>

	<!-- Fractions, Roots & Arrows -->
	<div class="w-full">
		<h2 class="mb-2 text-xl font-semibold">Fractions &amp; Roots</h2>
		<pre class="p-4">
\frac&#123;a&#125;&#123;b&#125;
\sqrt&#123;x&#125;, \sqrt[n]&#123;x&#125;
\frac&#123;dy&#125;&#123;dx&#125;
    </pre>

		<h3 class="mb-2 font-semibold">Arrows</h3>
		<pre class="p-4">
\to, \leftarrow, \uparrow,
\Rightarrow, \Leftarrow, 
\iff, \implies, \mapsto,
\longrightarrow, \downarrow
    </pre>
	</div>

</div>
