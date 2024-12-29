import React, { useState } from 'react';
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { Tabs, TabsList, TabsTrigger, TabsContent } from "@/components/ui/tabs";
import { LineChart, Line, XAxis, YAxis, CartesianGrid, Tooltip, ResponsiveContainer } from 'recharts';
import { Bell, CreditCard, Settings, Users, Calendar, DollarSign, RefreshCcw } from 'lucide-react';

// Mock Data
const mockTransactions = [
  { id: 1, date: '2024-12-27', amount: 12500, type: 'Payment', merchant: 'AWS Cloud Services', status: 'Completed' },
  { id: 2, date: '2024-12-27', amount: 5000, type: 'Subscription', merchant: 'Microsoft 365', status: 'Pending' },
  { id: 3, date: '2024-12-26', amount: 25000, type: 'Transfer', merchant: 'Internal Treasury', status: 'Completed' },
];

const mockSpendingData = [
  { month: 'Jul', amount: 45000 },
  { month: 'Aug', amount: 52000 },
  { month: 'Sep', amount: 49000 },
  { month: 'Oct', amount: 63000 },
  { month: 'Nov', amount: 58000 },
  { month: 'Dec', amount: 72000 },
];

const mockSubscriptions = [
  { id: 1, name: 'AWS Cloud Services', amount: 12500, renewalDate: '2025-01-27', status: 'Active' },
  { id: 2, name: 'Microsoft 365', amount: 5000, renewalDate: '2025-01-15', status: 'Active' },
  { id: 3, name: 'Salesforce Enterprise', amount: 8000, renewalDate: '2025-01-10', status: 'Active' },
];

const Dashboard = () => {
  const [activeTab, setActiveTab] = useState('overview');

  return (
    <div className="min-h-screen bg-gray-50 p-8">
      <div className="max-w-7xl mx-auto">
        {/* Header */}
        <div className="flex justify-between items-center mb-8">
          <div>
            <h1 className="text-3xl font-bold text-gray-900">Enterprise Wallet</h1>
            <p className="text-gray-500">Welcome back, Enterprise Admin</p>
          </div>
          <div className="flex gap-4">
            <Bell className="w-6 h-6 text-gray-500" />
            <Settings className="w-6 h-6 text-gray-500" />
          </div>
        </div>

        {/* Quick Stats */}
        <div className="grid grid-cols-1 md:grid-cols-4 gap-4 mb-8">
          <Card>
            <CardContent className="flex items-center p-6">
              <DollarSign className="w-8 h-8 text-blue-500 mr-4" />
              <div>
                <p className="text-sm text-gray-500">Total Balance</p>
                <p className="text-2xl font-bold">$245,000</p>
              </div>
            </CardContent>
          </Card>
          <Card>
            <CardContent className="flex items-center p-6">
              <RefreshCcw className="w-8 h-8 text-green-500 mr-4" />
              <div>
                <p className="text-sm text-gray-500">Monthly Spend</p>
                <p className="text-2xl font-bold">$72,000</p>
              </div>
            </CardContent>
          </Card>
          <Card>
            <CardContent className="flex items-center p-6">
              <Calendar className="w-8 h-8 text-purple-500 mr-4" />
              <div>
                <p className="text-sm text-gray-500">Active Subscriptions</p>
                <p className="text-2xl font-bold">8</p>
              </div>
            </CardContent>
          </Card>
          <Card>
            <CardContent className="flex items-center p-6">
              <Users className="w-8 h-8 text-orange-500 mr-4" />
              <div>
                <p className="text-sm text-gray-500">Team Members</p>
                <p className="text-2xl font-bold">12</p>
              </div>
            </CardContent>
          </Card>
        </div>

        {/* Main Content */}
        <Tabs value={activeTab} onValueChange={setActiveTab} className="space-y-4">
          <TabsList>
            <TabsTrigger value="overview">Overview</TabsTrigger>
            <TabsTrigger value="transactions">Transactions</TabsTrigger>
            <TabsTrigger value="subscriptions">Subscriptions</TabsTrigger>
          </TabsList>

          <TabsContent value="overview">
            <Card>
              <CardHeader>
                <CardTitle>Spending Overview</CardTitle>
              </CardHeader>
              <CardContent>
                <div className="h-[300px]">
                  <ResponsiveContainer width="100%" height="100%">
                    <LineChart data={mockSpendingData}>
                      <CartesianGrid strokeDasharray="3 3" />
                      <XAxis dataKey="month" />
                      <YAxis />
                      <Tooltip />
                      <Line type="monotone" dataKey="amount" stroke="#2563eb" />
                    </LineChart>
                  </ResponsiveContainer>
                </div>
              </CardContent>
            </Card>
          </TabsContent>

          <TabsContent value="transactions">
            <Card>
              <CardHeader>
                <CardTitle>Recent Transactions</CardTitle>
              </CardHeader>
              <CardContent>
                <div className="space-y-4">
                  {mockTransactions.map((transaction) => (
                    <div key={transaction.id} className="flex items-center justify-between p-4 bg-white border rounded-lg">
                      <div className="flex items-center">
                        <CreditCard className="w-6 h-6 text-gray-400 mr-4" />
                        <div>
                          <p className="font-medium">{transaction.merchant}</p>
                          <p className="text-sm text-gray-500">{transaction.date}</p>
                        </div>
                      </div>
                      <div className="text-right">
                        <p className="font-medium">${transaction.amount.toLocaleString()}</p>
                        <p className={`text-sm ${
                          transaction.status === 'Completed' ? 'text-green-500' : 'text-orange-500'
                        }`}>
                          {transaction.status}
                        </p>
                      </div>
                    </div>
                  ))}
                </div>
              </CardContent>
            </Card>
          </TabsContent>

          <TabsContent value="subscriptions">
            <Card>
              <CardHeader>
                <CardTitle>Active Subscriptions</CardTitle>
              </CardHeader>
              <CardContent>
                <div className="space-y-4">
                  {mockSubscriptions.map((subscription) => (
                    <div key={subscription.id} className="flex items-center justify-between p-4 bg-white border rounded-lg">
                      <div>
                        <p className="font-medium">{subscription.name}</p>
                        <p className="text-sm text-gray-500">Renews: {subscription.renewalDate}</p>
                      </div>
                      <div className="text-right">
                        <p className="font-medium">${subscription.amount.toLocaleString()}/month</p>
                        <p className="text-sm text-green-500">{subscription.status}</p>
                      </div>
                    </div>
                  ))}
                </div>
              </CardContent>
            </Card>
          </TabsContent>
        </Tabs>
      </div>
    </div>
  );
};

export default Dashboard;
