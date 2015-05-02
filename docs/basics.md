# Kelp basics (non-themable)

## Layout
### kelp-flex
Flexbox with a default basis of 12. Here is an example of how it would look like with the basis set
```
| 1/2 basis: 12 | 1/2 basis: 12 | (total: 24)
| 1/3 basis: 12 | 1/3 basis: 12 | 1/3 basis: 12 | (total: 36)
| 2/3 basis: 12 | 1/3 basis: 6 | (total: 18)
| 3/4 basis: 12 | 1/4 basis: 4 | (total: 16)
| 60% basis: 12 | 20% basis: 4 | 20% basis: 4 | (total: 20)
| 50% basis: 12 | 16.6% basis: 4 | 16.6% basis: 4 | 16.6% basis: 4 | (total: 24)
```

Classes:
- kelp-flex-row
- kelp-flex-col
- kelp-flex-box
- kelp-flex-box-[n] (where n is flex-basis; available for evens below 12 and some above 12: 2, 4, 6, 8, 10, 12, 18, 24, 36)
