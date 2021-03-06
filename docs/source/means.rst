Mean Functions
===============

The package provides functions to compute means of different kinds.

- **geomean** (x)

  Compute the geometric mean of ``x``.

- **harmmean** (x)

  Compute the harmonic mean of ``x``.

- **trimmean** (x, p)

  Compute the trimmed mean of ``x``, with fraction ``p`` of elements ignored.

  **Examples:**

  .. code-block:: julia

    # computes the mean using 80% of the numbers in ``x``, 
    # ignoring 10% of the largest and 10% of the smallest values.

    trimmean(x, 0.2)

- **mean** (x, w)

  The ``mean`` function is also extended to accept a weight vector of type ``WeightVec`` (see :ref:`weightvec`) to compute weighted mean. 

  **Examples:**

  .. code-block:: julia

    w = rand(n)
    x = mean(x, weights(w))

- **mean** (x, w, dim)

  Compute weighted means along a certain dimension.

  Here, ``x`` is a matrix, ``w`` is a weight vector of type ``WeightVec``, and ``dim`` should be either ``1`` or ``2``. 

  Suppose the size of ``x`` is ``(m, n)``: 

  - when ``dim = 1``: it computes weighted mean along each column (across rows). ``length(w)`` should be ``m``, and it returns an array of size ``(1, n)``.

  - when ``dim = 2``: it computes weighted mean along each row (across columns). ``length(w)`` should be ``n``, and it returns an array of size ``(m, 1)``. 

- **mean!** (dst, x, w, dim)

  Compute weighted means along a certain dimension, and write results to a pre-allocated destination vector ``dst``. 

  Here, ``length(dst)`` should be equal to either ``n`` or ``m``, when ``dim`` is ``1`` or ``2``.
