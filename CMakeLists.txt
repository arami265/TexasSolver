cmake_minimum_required(VERSION 3.16)

project(TexasSolverConsole LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

find_package(Qt5 REQUIRED COMPONENTS Core)
find_package(OpenMP)

add_executable(texassolver_console
    src/console.cpp
    src/Card.cpp
    src/Deck.cpp
    src/GameTree.cpp
    src/library.cpp
    src/compairer/Dic5Compairer.cpp
    src/experimental/TCfrSolver.cpp
    src/nodes/ActionNode.cpp
    src/nodes/ChanceNode.cpp
    src/nodes/GameActions.cpp
    src/nodes/GameTreeNode.cpp
    src/nodes/ShowdownNode.cpp
    src/nodes/TerminalNode.cpp
    src/ranges/PrivateCards.cpp
    src/ranges/PrivateCardsManager.cpp
    src/ranges/RiverCombs.cpp
    src/ranges/RiverRangeManager.cpp
    src/runtime/PokerSolver.cpp
    src/solver/BestResponse.cpp
    src/solver/CfrSolver.cpp
    src/solver/PCfrSolver.cpp
    src/solver/Solver.cpp
    src/tools/CommandLineTool.cpp
    src/tools/GameTreeBuildingSettings.cpp
    src/tools/lookup8.cpp
    src/tools/PrivateRangeConverter.cpp
    src/tools/progressbar.cpp
    src/tools/Rule.cpp
    src/tools/StreetSetting.cpp
    src/tools/utils.cpp
    src/trainable/CfrPlusTrainable.cpp
    src/trainable/DiscountedCfrTrainable.cpp
    src/trainable/DiscountedCfrTrainableHF.cpp
    src/trainable/DiscountedCfrTrainableSF.cpp
    src/trainable/Trainable.cpp
)

target_include_directories(texassolver_console
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}
        ${CMAKE_CURRENT_SOURCE_DIR}/include
)

target_link_libraries(texassolver_console
    PRIVATE
        Qt5::Core
)

if(OpenMP_CXX_FOUND)
    target_link_libraries(texassolver_console PRIVATE OpenMP::OpenMP_CXX)
endif()
