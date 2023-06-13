# mic3_Problem-set-2
VoIP Call Analysis

This analysis focuses on calculating various metrics related to Voice over IP (VoIP) calls using the provided dataset. The dataset contains information about the start time, end time, MSISDN (Mobile Station International Subscriber Directory Number), uplink volume, downlink volume, and domain/app of each call.
Steps for Analysis

    Select each MSISDN: Unique MSISDN values are retrieved from the dataset by removing duplicates.

    Select specific start and end datetime domain/app wise: The dataset is filtered based on specific start and end datetime values for each domain/app.

    Identify each single call for each VoIP App:
        Start time (ST) and end time (ET) are calculated for each record.
        ET*(ET-10 min) is calculated to exclude idle time of 10 minutes.
        If ET-10 min < ST, the original ET is kept.

    Calculate total volume of each call of each domain: The total volume of each call is calculated by summing the uplink (UL) and downlink (DL) volumes of all records in kilobytes (KB).

    Calculate total time of each call of each VoIP App: The highest ET and lowest ST among the respective records are identified for each call. The difference between these times is calculated in seconds to determine the total time of each call.

    Calculate bit rate (kbps) of each call of each VoIP App: The bit rate is calculated by dividing the total volume of each call by the total time of each call in kilobits per second (kbps).

    Identification of audio or video call and its count:
        Calls with a bit rate (kbps) less than 10 kbps are discarded.
        Assuming calls with a bit rate <= 200 kbps are classified as audio calls, and calls with a bit rate > 200 kbps are classified as video calls.

Output

The analysis generates the following columns in the output:

    MSISDN: The unique mobile number associated with each call.
    Domain: The domain/app of each call.
    Duration (sec): The duration of each call in seconds.
    FDR Count: The number of CDRs (Call Detail Records) required to make a single call.
    Bit Rate (kbps): The calculated bit rate of each call in kilobits per second.
    isAudio: Indicates whether the call is classified as an audio call.
    isVideo: Indicates whether the call is classified as a video call.
