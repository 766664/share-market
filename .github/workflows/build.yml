package com.kiranchaure.sharemarket

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.foundation.layout.*
import androidx.compose.foundation.lazy.LazyColumn
import androidx.compose.foundation.lazy.items
import androidx.compose.material3.*
import androidx.compose.runtime.*
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.unit.dp

data class Signal(
    val name: String,
    val signal: String,
    val reason: String
)

class MainActivity : ComponentActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        setContent {
            ShareMarketApp()
        }
    }
}

@OptIn(ExperimentalMaterial3Api::class)
@Composable
fun ShareMarketApp() {

    var selectedTab by remember { mutableStateOf(0) }

    val signals = listOf(
        Signal(
            "SENSEX",
            "WAIT",
            "Trend confirmation ka wait"
        ),
        Signal(
            "NIFTY",
            "EARLY BUY",
            "Volume + trend strength bullish"
        ),
        Signal(
            "BANK NIFTY",
            "EARLY SELL",
            "Resistance + bearish structure"
        )
    )

    Scaffold(
        topBar = {
            TopAppBar(
                title = {
                    Column {
                        Text("SHARE MARKET")
                        Text(
                            "KIRAN CHAURE",
                            style = MaterialTheme.typography.labelSmall
                        )
                    }
                }
            )
        },
        bottomBar = {
            NavigationBar {

                NavigationBarItem(
                    selected = selectedTab == 0,
                    onClick = { selectedTab = 0 },
                    icon = { Text("⌂") },
                    label = { Text("Home") }
                )

                NavigationBarItem(
                    selected = selectedTab == 1,
                    onClick = { selectedTab = 1 },
                    icon = { Text("▥") },
                    label = { Text("Chart") }
                )

                NavigationBarItem(
                    selected = selectedTab == 2,
                    onClick = { selectedTab = 2 },
                    icon = { Text("⚙") },
                    label = { Text("Settings") }
                )
            }
        }
    ) { padding ->

        when (selectedTab) {

            0 -> HomeScreen(
                signals = signals,
                modifier = Modifier.padding(padding)
            )

            1 -> ChartScreen(
                modifier = Modifier.padding(padding)
            )

            2 -> SettingsScreen(
                modifier = Modifier.padding(padding)
            )
        }
    }
}

@Composable
fun HomeScreen(
    signals: List<Signal>,
    modifier: Modifier = Modifier
) {

    LazyColumn(
        modifier = modifier
            .fillMaxSize()
            .padding(16.dp),
        verticalArrangement = Arrangement.spacedBy(12.dp)
    ) {

        item {
            Text(
                "Market Analysis",
                style = MaterialTheme.typography.headlineSmall
            )
        }

        item {
            Text(
                "Early trend-change alert system",
                style = MaterialTheme.typography.bodyMedium
            )
        }

        item {
            Card(
                modifier = Modifier.fillMaxWidth()
            ) {
                Column(
                    modifier = Modifier.padding(16.dp)
                ) {

                    Text(
                        "5-Minute Early Alert",
                        style = MaterialTheme.typography.titleMedium
                    )

                    Spacer(Modifier.height(8.dp))

                    Text(
                        "Trend change ke possible signs detect hone par " +
                                "early warning generate ki jayegi."
                    )

                    Spacer(Modifier.height(8.dp))

                    Text("BUY / SELL / WAIT")
                }
            }
        }

        items(signals) { item ->

            SignalCard(item)
        }
    }
}

@Composable
fun SignalCard(signal: Signal) {

    Card(
        modifier = Modifier.fillMaxWidth()
    ) {

        Column(
            modifier = Modifier.padding(16.dp)
        ) {

            Text(
                signal.name,
                style = MaterialTheme.typography.titleLarge
            )

            Spacer(Modifier.height(6.dp))

            Text(
                signal.signal,
                style = MaterialTheme.typography.titleMedium
            )

            Spacer(Modifier.height(6.dp))

            Text(
                "Reason: ${signal.reason}"
            )
        }
    }
}

@Composable
fun ChartScreen(
    modifier: Modifier = Modifier
) {

    Column(
        modifier = modifier
            .fillMaxSize()
            .padding(16.dp),
        horizontalAlignment = Alignment.CenterHorizontally
    ) {

        Text(
            "Live Market Chart",
            style = MaterialTheme.typography.headlineSmall
        )

        Spacer(Modifier.height(20.dp))

        Card(
            modifier = Modifier
                .fillMaxWidth()
                .height(300.dp)
        ) {

            Box(
                modifier = Modifier.fillMaxSize(),
                contentAlignment = Alignment.Center
            ) {

                Text(
                    "LIVE CHART\n\nAngel One SmartAPI data yahan aayega"
                )
            }
        }

        Spacer(Modifier.height(16.dp))

        Text("Timeframe: 1m | 5m | 10m | 15m")
    }
}

@Composable
fun SettingsScreen(
    modifier: Modifier = Modifier
) {

    var earlyAlert by remember { mutableStateOf(true) }
    var orderBlock by remember { mutableStateOf(true) }
    var liquidity by remember { mutableStateOf(true) }
    var autoOrder by remember { mutableStateOf(false) }

    LazyColumn(
        modifier = modifier
            .fillMaxSize()
            .padding(16.dp)
    ) {

        item {
            Text(
                "Settings",
                style = MaterialTheme.typography.headlineSmall
            )

            Spacer(Modifier.height(16.dp))
        }

        item {
            SettingSwitch(
                "5-Minute Early Alert",
                earlyAlert
            ) {
                earlyAlert = it
            }
        }

        item {
            SettingSwitch(
                "Order Block",
                orderBlock
            ) {
                orderBlock = it
            }
        }

        item {
            SettingSwitch(
                "Liquidity Detection",
                liquidity
            ) {
                liquidity = it
            }
        }

        item {
            SettingSwitch(
                "Automatic Order",
                autoOrder
            ) {
                autoOrder = it
            }
        }

        item {
            Spacer(Modifier.height(20.dp))

            Text(
                "Automatic Order default: OFF",
                style = MaterialTheme.typography.bodyMedium
            )
        }
    }
}

@Composable
fun SettingSwitch(
    title: String,
    checked: Boolean,
    onCheckedChange: (Boolean) -> Unit
) {

    Row(
        modifier = Modifier
            .fillMaxWidth()
            .padding(vertical = 8.dp),
        verticalAlignment = Alignment.CenterVertically
    ) {

        Text(
            title,
            modifier = Modifier.weight(1f)
        )

        Switch(
            checked = checked,
            onCheckedChange = onCheckedChange
        )
    }
}
