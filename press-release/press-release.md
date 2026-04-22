# Tomorrow's Air: A Machine Learning Tool That Predicts Whether the Air You Breathe Will Be Safe

Everday you step outside, you're taking a guess on the air quality. This tool ends that guessing.

Every morning, we step outside without knowing whether the air they're about to breathe could trigger an asthma attack, worsen a heart condition, or harm a child's developing lungs. For most people, air quality is invisible. You can't see it, smell it, or feel it until the damage is already done. And by the time an alert shows up on your phone, the bad air day has already begun. For the 28 million Americans living with asthma, the millions more with heart disease, the elderly, and young children, there is still no reliable way to know tomorrow whether it's safe to go outside.

This project builds a machine learning model trained on daily EPA air quality observations from five major US cities, covering two full years of data. The model learns the patterns between measurable conditions, such as fine particle levels, ozone, nitrogen dioxide, and other pollutants, and makes a decision on what the air quality will look like the following day. Instead of outputting a confusing number, the model would classify the air wuality as Good, Moderate, Unhealthy for Sensitive Groups, Unhealthy, or Very Unhealthy. The goal is to give vulnerable people the time to prepare.

![Chart](images/press-release-image-aqi.png)

Figure 1. Distribution of daily AQI categories across Los Angeles, New York, Houston, Chicago, and Phoenix from 2022 to 2023. While most days fall in the "Good" category, nearly 1,000 days per year across these cities register conditions that pose measurable health risks, particularly for people with asthma, heart disease, the elderly, and children.
