# mh5_cad - CAD files, including STLs for MH5 robot

[![Version](https://img.shields.io/badge/Rev-F-blue)](https://img.shields.io/badge/master-0.2.0-blue)

The 3D design of the robot is maintained in [onshape](https://cad.onshape.com/documents/1b88afa68bb97584375e284c/w/8d3aebf9e78687fc1b4a5d80/e/6f5b4ad05cdba68c2c42dd17).

The parts bellow are for the Revision F model of the MH5 humanoid robot.

## Printing BOM

| Item | Description | Final | Qty | Comments |
|------|-------------|-------|-----|----------|
| [Foot-Sole](STL/Foot-Sole.stl) | Sole for the FSR feet                   | Yes | 2 | one for each foot
| [Foot-Top](STL/Foot-Top.stl)   | Upper part of FSR feel                  | Yes | 2 | one for each foot
| [Foot-Back](STL/Foot-Back.stl) | Back side of the FSR foot, uses magnets | Yes | 2 | one for each foot
| [Ankle](STL/Ankle.stl)         | Frame for ankle                         | Yes | 4 | 2 for each foot
| [MH5-F02](STL/MH5-F02.stl)     | Stright U frame                         | Yes | 4 | 2 used in feet (1 each) and 2 used in arms (1 each)
| [MH5-F03](STL/MH5-F03.stl)     | Bottom of servo frame                   | Yes | 6 | 3 for each arm
| [MH5-F04](STL/MH5-F04.stl)     | Curved U frame                          | Yes | 4 | 2 used in hips and 2 in shoulders
| [MH5-F05](STL/MH5-F05.stl)     | Thigh frame                             | Yes | 2 | one in each foot
| [Hand-Left](STL/Hand-Left.stl) | Anatomic left hand                      | Yes | 1 |
| [Hand-Right](STL/Hand-Right.stl) | Anatomic right hand                   | Yes | 1 |
| [Chest](STL/Chest.stl)         | Chest main frame                        | Yes | 1 |
| [Front](STL/Front.stl)         | Front chest cover                       | Yes | 1 |
| [Neck](STL/Neck.stl)           | Neck                                    | Yes | 1 |
| [Head-Back](STL/Head-Back.stl) | Back side of the head                   | Yes | 1 |
| [Head-Front](STL/Head-Front.stl) | Front side of the head                | Yes | 1 |
| [Head-Camera-Cover](STL/Head-Camera-Cover.stl) | Cover for cameras.      | Yes | 2 | One for each mini camera

## Assembly preparation

Before assembly you must configure the Dynamixel Servos as described in [Configuring servos](DOCS/servos.md).

You should also get familiar with the [installation of heat-serts](DOCS/assembly-heatserts.md). There will several steps in the following instructions where you will have to perform this activity.

Quite a few number of servos in this robot make use of the new through-the-idler wiring of the cables that produces a tidier cabling and reduces the stress and the risk of cables being severed by frame collision. You should be familiar with the instructions provided by Robotis for both the [XL430](https://emanual.robotis.com/docs/en/dxl/x/xl430-w250/#idler-horn-assembly) and the [2XL430](https://emanual.robotis.com/docs/en/dxl/x/2xl430-w250/#idler-horn-assembly) servos.

## Sub-groups Assembly

[**Leg assembly**](DOCS/assembly-legs.md) is almost identical for left and right because the 2-axis servomotors make impossible mirror assembly. The only difference is the way the feet are connected to the ankles and this is explicitly described in the instructions.

[**Arms assembly**](DOCS/assembly-arms.md) is symmetrical so that cables are following a consistent pattern (on the inside or on the outside of the assembly, but similar between left and right). The instructions describe these activities in detail.

[**Torso and neck**](DOCS/assembly-torso.md) assembly describes the assembly of the fixed components to the torso.

In [**Full assembly**](DOCS/assembly-full.md) the sub-assemblies prepared earlier as well as the electronic components are put together to produce the full robot.
