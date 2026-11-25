# SRG-7C91: A zero spectral marginal with positive asymptotic wire cost

**Research note — November 25, 2026**  
**Attribution:** magoodin1992-ux; AI-assisted mathematical research and exposition.  
**Status:** scoped mathematical derivation, not peer reviewed or Lean-formalized.

## Abstract

For the Euclidean tensor spectral price of a shared coherent label, adding a receiver within the convex hull of existing receivers leaves its mean-width price unchanged. We show that this invariance does not extend to the optimal asymptotic cost of realizing the label from independent pairwise identity wires. For a unit equilateral triangle, demanding an additional output at its centroid increases that cost per bit from \(3/2\) to \(1+1/\sqrt3\), although the spectral price remains \(3/2\). The gap is exact within the declared resource model. This example separates spectral redundancy from constructive resource redundancy.

## Model

Let \(S=\{a,b,c\}\) be the vertices of a unit equilateral triangle, and let \(z\) be its centroid. The allowed sites are \(a,b,c,z\) throughout. A wire between sites \(u,v\) is an independent two-party identity tensor of integer dimension \(q\ge1\). Its cost is \(\|u-v\|\log_2 q\). The product of purchased wires may be restricted using arbitrary local linear maps over a common coefficient field. There is no charge in this model for the descriptions or evaluation of these local maps.

The required output at a terminal set \(U\) is the common-label tensor
\[
D_U(K)=\sum_{j=1}^K \bigotimes_{u\in U}e_j,
\]
with scalar output at other sites. Define \(L_U(m)\) to be the infimum of purchased wire cost for an exact output \(D_U(2^m)\). We compare limiting cost per output bit as \(m\to\infty\). This is a tensor restriction model, not a deterministic physical communication protocol or a thermodynamic energy model.

## Proposition

Using the mean-width normalization in the November 24, 2026 Euclidean tensor spectral geometry manuscript, the shared-label spectral price per bit for either terminal set is \(3/2\). Yet
\[
\lim_{m\to\infty}L_S(m)/m=3/2,\qquad
\lim_{m\to\infty}L_{S\cup\{z\}}(m)/m=1+1/\sqrt3.
\]
In particular the exact incremental wire cost is \(1/\sqrt3-1/2>0\).

## Proof: spectral value

The normalized mean width of a planar convex polygon is half its perimeter. The convex hull of the triangle is unchanged by inserting its centroid. Thus the shared-label mean-width price is \(3/2\) per bit in both cases, by the cited spectral pricing theorem. This part uses the external manuscript's normalization and theorem; it is not a new derivation of that theorem.

## Proof: lower bounds

Across any cut separating demanded terminals, the target flattening has rank \(2^m\). The source product of identity wires has flattening rank equal to the product of the dimensions of the crossing wires. Local linear restrictions cannot increase this rank. Consequently the sum of logarithmic wire dimensions across each such cut is at least \(m\).

Write \(X\) for the sum of logarithmic dimensions on triangle rim edges and \(Y\) for the sum on centroid spokes. Multiple wires can be grouped by tensor product. Every rim edge has length 1 and every spoke has length \(1/\sqrt3\). The cost is \(X+Y/\sqrt3\).

Summing the three singleton cuts at the triangle vertices gives \(2X+Y\ge3m\). Hence
\[
X+Y/\sqrt3\ge3m/2+(1/\sqrt3-1/2)Y\ge3m/2.
\]
When the centroid is demanded as well, its singleton cut requires \(Y\ge m\). Therefore the cost is at least \((1+1/\sqrt3)m\).

## Proof: matching asymptotic constructions

For a fixed cycle of \(k\ge3\) sites, independent dimension-\(d\) wires around the cycle can be restricted to a common label of size \(d^{2-o(1)}\) as \(d\to\infty\), over any coefficient field. Here is a label-selection proof.

Use integer wire labels \(i_1,\ldots,i_k\) from \([1,d]\). Put \(N=\lfloor d/k\rfloor\). Choose \(B\subseteq[1,N]\) of size \(N\exp[-O_k(\sqrt{\log N})]\) with no nonconstant average of \(k-1\) of its elements belonging to \(B\). Such sets follow by the sphere construction: encode equal-squared-norm digit vectors with digits in \(\{0,\ldots,a-1\}\) in base \((k-1)a\), choose the most populated sphere, and take the digit count and \(\log a\) of order \(\sqrt{\log N}\). There are no carries in the average equation; strict convexity forces all digit vectors to agree. Translation places the resulting integers in the positive range.

At each of the first \(k-1\) cycle vertices keep a pair only when \(i_{j+1}-i_j\in B\). At the closing vertex keep a pair only when \(i_k-i_1\in(k-1)B\). The no-average property forces all successive differences to equal one common \(b\in B\). Every retained local pair identifies the full tuple \((i_1,b)\), including at the closing vertex. Relabel the retained pairs by that tuple, mapping other basis vectors to zero. The surviving sum is exactly diagonal. At least \(N|B|\) tuples survive by restricting \(i_1\) to \([1,N]\). These are integer index selections, independent of coefficient-field arithmetic.

Thus the cost per common bit of a cycle with perimeter \(P\) approaches \(P/2\). For any sufficiently large requested output \(2^m\), choose a sufficiently large wire dimension with \(\log_2 d=m/2+O_k(\sqrt m+1)\), then restrict excess common labels away. The cost approaches \(P/2\) per bit.

For \(S\), use the triangle cycle, of perimeter 3. For \(S\cup\{z\}\), use the cycle \(a,b,c,z,a\), of perimeter \(2+2/\sqrt3\). These match the respective lower bounds. \(\square\)

## Significance and limitations

The example distinguishes an invariant lower bound from achievable construction cost. Equality of scalar spectral prices does not establish interchangeability under changes of terminal requirements. The local maps are not assumed to have efficient circuit descriptions. This is an asymptotic exact-restriction result, not a claim about a one-shot protocol, arbitrary tensor resources, physical energy, or general computational complexity. The proof above is confined to the four specified sites. Historical novelty is not asserted.

## References

- OpenAI, *Euclidean geometry in the asymptotic spectrum of tensors*, November 24, 2026. [Pinned manuscript](https://github.com/openai/math/blob/92b516ef8e2abf66c3db7aa31438d3010bc7956f/preprints/Euclidean-geometry-in-the-asymptotic-spectrum-of-tensors-November-24-2026/paper.pdf). Source of the spectral pricing comparison.
- P. Vrana and M. Christandl, *Entanglement distillation from Greenberger–Horne–Zeilinger shares*, [arXiv:1603.03964](https://arxiv.org/abs/1603.03964). Antecedent for graph-tensor asymptotic conversion.
- F. A. Behrend, *On sets of integers which contain no three terms in arithmetical progression*, Proc. Natl. Acad. Sci. USA 32 (1946), 331–332. Antecedent for the digit-sphere construction.

## License and citation

This research note is made available under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/), to the extent rights are held by the publisher. External works retain their own terms.

Suggested citation: magoodin1992-ux, “SRG-7C91: A zero spectral marginal with positive asymptotic wire cost,” November 25, 2026, this repository.
