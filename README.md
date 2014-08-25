## Data Collector Sample for Visual Studio Test Platform

A bare bones data collector implementing Session and TestCase events.

## Deployment

Copy the built binaries to `$env:ProgramFiles(x86)\Microsoft Visual Studio 12.0\Common7\IDE\PrivateAssemblies\DataCollectors`

## Running the sample

Create a `runsettings` file with following data collector specification:

    <!-- Configurations for data collectors -->
    <DataCollectionRunSettings>
        <DataCollectors>
          <DataCollector uri="datacollector://SampleDataCollector/1.0" assemblyQualifiedName="VSTest.Samples.DataCollector.SampleDataCollector, VSTest.Samples.DataCollector, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" friendlyName="SampleDataCollector">
          </DataCollector>
        </DataCollectors>
    </DataCollectionRunSettings>
    
Run any test on a `Developer Command Prompt` with settings file:

    vstest.console UnitTestProject1.dll /settings:sample.runsettings

    Microsoft (R) Test Execution Command Line Tool Version 12.0.30501.0
    Copyright (c) Microsoft Corporation.  All rights reserved.

    Starting test execution, please wait...
    Warning: Using Isolation mode to run the tests as diagnostic data adapters were enabled in the runsettings. Use the /inIsolation parameter to suppress this warning.
    Warning: Diagnostic data adapter ('Sample data collector') message: SampleAdapter: Session start. Session id: {1ba5eb4f-801e-48b2-b3c2-a44f3ec9a431}.

    Warning: Diagnostic data adapter ('Sample data collector') message: SampleAdapter: Test Case start. Test case name: UnitTestProject1.UnitTest1.TestMethod1.

    Warning: Diagnostic data adapter ('Sample data collector') message: SampleAdapter: Test Case end. Test case end: UnitTestProject1.UnitTest1.TestMethod1.

    Passed   TestMethod1

    Total tests: 1. Passed: 1. Failed: 0. Skipped: 0.
    Test Run Successful.
    Test execution time: 0.2830 Seconds
    Warning: Diagnostic data adapter ('Sample data collector') message: SampleAdapter: Session end. Session id: {1ba5eb4f-801e-48b2-b3c2-a44f3ec9a431}.
