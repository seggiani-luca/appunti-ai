# Computer vision: introduction, image formation and properties

## Sensors and feature extraction
We obtain images through *sensors* (like the ones in cameras)
Sensors can be:
- Passive:
- Active:
Input from sensors is *noisy*
We intend to extract *features*

Two model-based approaches:
- Object model: description of the object itself ("What _is_ it?") 
- Rendering model: description of how the object appears to the sensors ("What does it _look_ like?")

Two tasks we might want to accomplish:
- Reconstruction: building the model itself
- Recognition: drawing distinctions between objects

## Images: arrays of pixels
How does the sensor actually _sense_ an image?
- Eyes discern images by gathering light on *photoreceptors*:
    - *Cones*, which sense *_color_* and work best in *bright light*
    - *Rods*, which sense *_luminance_* and work best in *low light*

- Analog cameras create images by projecting light onto *film* coated with photosensitive silver halides

- Digital cameras sense images as a *2D array of pixels* (_picture elements_)
    - Each pixels contains color information, usually encoded with 8 bits per channel (24 bits total for RGB) 

## Sensing images: CCD and CMOS arrays
To sense images, we need arrays of sensors, which can be:
- CCD (_Charge-Coupled Devices_)
- CMOS (_Complementary Metal-Oxide Semiconductor_)

When photons hit the sensors, they emit an *electrical signal*:
- The signal is proportional to *intensity* (number of photons hitting the sensor)
- The sensor's response to wavelength dependes on a *color filter array* (e.g. Bayer Filter), which splits lights into RGB channels
- The measurement is weighted over some time window (exposure time)

## Pinhole cameras
A very simple camera is formed by a *camera obscura* (_a box_) with an *aperture* (_an opening_)
- If the opening is small enough, we get a picture on the *image plane* (_the side of the box opposite to the opening_)

Let $f$ be the distance between the aperture and the image plane.
Then, through similar triangles:
$$
\frac{-x}{f} = \frac{X}{Z}, \ \frac{-y}{f} = \frac{Y}{Z} \implies x = \frac{-fX}{Z}, \ y = \frac{-fY}{Z}
$$
where:
- $x, y$ are coordinates on the image plane 
- $X, Y, Z$ are coordinates of an object in space, with $Z$ being the distance of the object from the camera 

Note that:
- The negative sign means *inverted* projection
- As $Z \rightarrow \infty$:
$$
\lim_{Z \rightarrow \infty} \left( \frac{-fX}{Z}, \frac{-fY}{Z} \right) = (0, 0)
$$
This is nothing but _foreshortening_ due to *perspective*

## Lens systems
Pinhole cameras are *dark*
We could get more light by enlarging the aperture, but then we would get *defocusing*
We solve the problem by introducing a *lens system*
- Eyes have lenses that deform to focus objects
- Cameras have systems of moving lenses that change their relative position

Lens systems introduce *distortion* and *depth of field*:
- Objects on the *focal plane* are focused
- The range of depths for which objects remain focused is the depth of field
- Around the edges, we experience _barrel distortion_ or _pin-cushion distortion_

## Scaled ortographic projection
A simpler model for vision is *scaled ortographic projection*
If objects fall in some depth $Z_0 \pm \Delta Z$ with $\Delta Z << Z_0$, we can approximate the $\frac{f}{Z}$ term with a constant $s = \frac{f}{z_0}$:
$$
x = sX \ y = sY
$$

- Scaled ortographic projection works for objects at _similar_ distances to the camera

## Image properties: light and shading
Which properties can be extracted from images?
The brigthness of pixels is proportional to the brightness of *surfaces*
A model for surface brightness is given by the *rendering equation*:
$$
L_o(x, \omega_0, \lambda, t) = L_e(x, \omega_0, \lambda, t) + L_r(x, \omega_0, \lambda, t)
$$
where:
- $L_o(x, \omega_0, \lambda t)$ is the intensity of light at position $x$, along direction $\omega_0$, at wavelength $\lambda$ and at time $t$
- $L_e(x, \omega_0, \lambda t)$ is the intensity of _emitted_ light
- $L_r(x, \omega_0, \lambda t)$ is the intensity of _reflected_ light

## Reflected light: diffuse and specular
The term we care most about is $L_r(x, \omega_0, \lambda, t)$, the *reflected light*
Let's assume the *distant point light source* approximation

There are different ways in which light can be reflected:
- *Diffuse* reflection: light is scattered evenly by rough surfaces
  A model is *Lambert's cosine law*:
  $$
  I_d = \rho I_0 \cos(\theta)
  $$
  where:
  - $I_d$ is the lambertian diffuse brightness
  - $I_0$ is the intensity of the light source
  - $\rho$ is the diffuse *albedo*
  - $\theta$ is the angle between the light source direction and the *surface normal*: $\cos(\theta) = \mathbf{L} \cdot \mathbf{n}$
- *Specular* reflection: light is "mirrored" based on the incident direction
  A model is *Phong specular reflection*:
  $$
  I_s = I_0 \cos(\theta')^n
  $$
  where:
  - $I_s$ is the Phong specular reflection
  - $I_0$ is the intensity of the light source
  - $\theta'$ is the angle between the *reflection direction* and the *view direction*: $\cos(\theta') = \mathbb{R} \cdot \mathbb{V}$, $\mathbb{R}$ is calculated based on incidence
  - $n$ is an empirical constant

Our model should also account for *shadows* and *ambient illumination*

Other phenomena might be present that doesn't fall into our model:
- Transmission
- Subsurface scattering
- Iridescence
- Polarization
- ...

## Color
We talked about _wavelengths_: in humans, light at different wavelengths gives the sensation of *color*
- Humans perceive wavelengths ranging from around 380nm (violet) to around 740nm (red)
- Cones in our retinas recognize *red*, *green* and *blue* (other colors are "filled in")

Cameras mimic human vision, using a Bayer Filter to recognize RGB colors
- This is usually enough for computer vision
- More advanced models might be sensitive to infrared or ultraviolet wavelengths

