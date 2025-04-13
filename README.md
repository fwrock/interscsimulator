# InterSCSimulator

This repository is a fork of the [Sim-Diasca Repository](https://github.com/Olivier-Boudeville-EDF/Sim-Diasca). Sim-Diasca is a parallel and distributed discrete-time simulation engine for complex systems. The name stands for 'Simulation of Discrete Systems of All Scales'. *This is the 2.2.11-rc4 version of Sim-Diasca*. Sim-Diasca is released under the LGPL license (GNU Lesser General Public License, version 3). Please refer to the `GPL-license.txt` and `LGPL-license.txt` files in the `sim-diasca/doc/common-elements/licence` directory.

See also: http://www.gnu.org/licenses/lgpl-3.0.html

Official Sim-Diasca website: http://sim-diasca.com.

A good starting point to understand how the engine should be used is to look in the `mock-simulators/smart_city_model/src` directory. Please refer to the 'Sim-Diasca Technical Manual' or the 'Sim-Diasca Developer Guide' for further information.

We hope you enjoy using Sim-Diasca!

In this repository, we add a [smart city model](https://github.com/fwrock/interscsimulator-smart-city-model) ([Main Repository](https://github.com/ezambomsantana/smart_city_model)). InterSCSimulator is based on Sim-Diasca, a general-purpose simulator implemented in Erlang.

## Running InterSCSimulator ##
1. Clone this repository:
  ```bash
  git clone git@github.com:fwrock/interscsimulator.git
  cd interscsimulator/
  ```

2. Go to the `mock-simulators/` directory and clone the smart city model from this [repository](https://github.com/fwrock/interscsimulator-smart-city-model):

```bash
cd mock-simulators/
git clone git@github.com:fwrock/interscsimulator-smart-city-model.git
  ```

3. Rename `interscsimulator-smart-city-model` to `smart_city_model`:
```bash
rm -r ./smart_city_model
mv interscsimulator-smart-city-model/ ./smart_city_model
```

4. Now, go to the root directory `interscsimulator/` and run the application using the Docker command.

5. Build the Docker image:
```bash
docker build -t interscsimulator .
```
6. Run the Docker container:

```bash
docker run -t -w /src/mock-simulators/smart_city_model/src -h {YOUR_HOSTNAME} -v {YOUR_VOLUME_OUTPUT_PATH}:/src/mock-simulators/smart_city_model/output -e USER=root -e CONFIG_PATH={YOUR_SCENARIO_CONFIG_PATH} interscsimulator
```

  - Example:
  ```bash
docker run -t -w /src/mock-simulators/smart_city_model/src -h teste.com -v /home/my_user/interscsimulator/output/base_scenario:/src/mock-simulators/smart_city_model/output -e USER=root -e CONFIG_PATH=/src/mock-simulators/smart_city_model/base_scenario/config.xml interscsimulator
```

### Notes

Checking the version of this source code and the source code version of the [smart city model](https://github.com/fwrock/interscsimulator-smart-city-model), make sure to select the same branch before running.
