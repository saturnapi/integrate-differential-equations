# integrate-differential-equations
API for integrate differential equations. Start using it, go to [saturnapi.com/artw/integrate-differential-equations](https://saturnapi.com/artw/integrate-differential-equations). 

Find more APIs or contribute at [SaturnAPI.com](https://saturnapi.com).

```
%%%%%%%%%%%%%%%%%%%%%%%%%% Integrating Differential Equations %%%%%%%%%%%%%%%%%%%%%%%%%%
% (GNU License)
% SaturnAPI has built-in functions for solving nonlinear differential equations of the form
%
%     dx
%     -- = f (x, t)
%     dt
%
% with the initial condition
%
%     x(t = t0) = x0
%
% For SaturnAPI to integrate equations of this form, 
% you must first provide a definition of the function f(x,t). 
% Do this by entering the function body directly in the API script. 
% The example script below defines the right-hand side function xdot
% for an interesting pair of nonlinear differential equations. 
% It computes the integral and prints the last term to be sent as the HTTP response data. 
% SaturnParams is an array containing the initial condition
% For instance, SaturnParams='[1 ; 2]'
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

function xdot = f (x, t)

  r = 0.25;
  k = 1.4;
  a = 1.5;
  b = 0.16;
  c = 0.9;
  d = 0.8;

  xdot(1) = r*x(1)*(1 - x(1)/k) - a*x(1)*x(2)/(1 + b*x(1));
  xdot(2) = c*a*x(1)*x(2)/(1 + b*x(1)) - d*x(2);

endfunction

x0 = SaturnParams;
t = linspace (0, 50, 200)';
x = lsode ("f", x0, t);

printf("%f", x(length(x)));
```
