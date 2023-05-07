import pandas as pd
import matplotlib.pyplot as plt

class MarketingAnalyticsSystem:
    def __init__(self):
        self.data = pd.DataFrame(columns=['Date', 'Campaign', 'Clicks', 'Conversions'])
    
    def collect_data(self, date, campaign, clicks, conversions):
        new_data = pd.DataFrame([[date, campaign, clicks, conversions]], columns=['Date', 'Campaign', 'Clicks', 'Conversions'])
        self.data = pd.concat([self.data, new_data], ignore_index=True)
    
    def process_data(self):
        self.data['Conversion Rate'] = self.data['Conversions'] / self.data['Clicks'] * 100
    
    def visualize_data(self):
        campaigns = self.data['Campaign'].unique()
        for campaign in campaigns:
            campaign_data = self.data[self.data['Campaign'] == campaign]
            plt.plot(campaign_data['Date'], campaign_data['Clicks'], label=f'{campaign} - Clicks')
            plt.plot(campaign_data['Date'], campaign_data['Conversions'], label=f'{campaign} - Conversions')
        plt.xlabel('Date')
        plt.ylabel('Count')
        plt.title('Marketing Performance')
        plt.legend()
        plt.show()
    
    def generate_report(self):
        report = self.data.groupby(['Campaign']).sum().reset_index()
        report['Conversion Rate'] = report['Conversions'] / report['Clicks'] * 100
        return report


# Example usage:

# Create a marketing analytics system
analytics_system = MarketingAnalyticsSystem()

# Collect data
analytics_system.collect_data('2023-01-01', 'Campaign A', 1000, 50)
analytics_system.collect_data('2023-02-01', 'Campaign A', 1200, 60)
analytics_system.collect_data('2023-03-01', 'Campaign B', 800, 40)
analytics_system.collect_data('2023-04-01', 'Campaign B', 900, 45)

# Process data
analytics_system.process_data()

# Visualize data
analytics_system.visualize_data()

# Generate report
report = analytics_system.generate_report()
print(report)
