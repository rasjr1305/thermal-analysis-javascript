# thermal-analysis-javascript

This is a package that allows users to simulate Laplace Thermal Rectangular Problems using
Javascript. Users need to input size of plate and boundary conditions, after calculation
the package returns the values of temperature along the domain and boundary.

```
////// SAMPLE USAGE
//////////////////////////////////////////
//*******RETANGULAR LAPLACE PROBLEMS SOLVER********//
//
//   SIDES OF RETANGULAR PLATE
//             t3,q3
//        ------3------
//        I           I
//        I           I
//  t4,q4 4           2 t2,q2
//        I           I
//        I           I
//        ------1------
//             t1,q1
//
import thermalRectangular from "thermal-analysis-javascript";

// INPUT TEMPERATURES OR FLUX ALONG THE BOUNDARIES
// INPUT TEMPERATURES OR FLUX ALONG DOWN SIDE OF PLATE
function t1(x, y) {
  return 0;
}
function q1(x, y) {
  return 0;
}
// INPUT TEMPERATURES OR FLUX ALONG RIGHT SIDE OF PLATE
function t2(x, y) {
  return 0;
}
function q2(x, y) {
  return 0;
}
// INPUT TEMPERATURES OR FLUX ALONG TOP SIDE OF PLATE
function t3(x, y) {
  return 0;
}
function q3(x, y) {
  return 10;
}
// INPUT TEMPERATURES OR FLUX ALONG LEFT SIDE OF PLATE
function t4(x, y) {
  return 1;
}
function q4(x, y) {
  return 0;
}

// NUMBER OF ELEMENTS PER SIDE, THE MORE ELEMENTS, MORE ACCURATE IS THE SOLUTION BUT MORE TIME TO SOLVE
const el = 16; // 16 ELEMENTS PER SIDE
const x0 = 1;  // WIDTH OF PLATE
const y0 = 3;  // HEIGHT OF PLATE
const bc1 = 0; // TYPE OF BOUNDARY CONDITION ON DOWN SIDE OF PLATE, 1 for TEMPERATURE 0 for FLUX
const bc2 = 1; // TYPE OF BOUNDARY CONDITION ON RIGHT SIDE OF PLATE , 1 for TEMPERATURE 0 for FLUX
const bc3 = 0; // TYPE OF BOUNDARY CONDITION ON TOP SIDE OF PLATE, 1 for TEMPERATURE 0 for FLUX
const bc4 = 1; // TYPE OF BOUNDARY CONDITION ON LEFT SIDE OF PLATE, 1 for TEMPERATURE 0 for FLUX

// MATRICE WITH INTERNAL POINTS DESIRED VALUES
const ip = [
  [0.5, 1.5],
  [0.5, 1.73465],
  [0.5, 1.96353],
];

let solution = thermalRectangular(
  el,
  x0,
  y0,
  bc1,
  bc2,
  bc3,
  bc4,
  t1,
  q1,
  t2,
  q2,
  t3,
  q3,
  t4,
  q4,
  ip
);

console.log(solution)
```
