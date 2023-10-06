package app.risqiikhsani

import androidx.compose.foundation.Image
import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.foundation.layout.*
import androidx.compose.material.Button
import androidx.compose.material.MaterialTheme
import androidx.compose.material.Surface
import androidx.compose.material.Text
import androidx.compose.runtime.Composable
import androidx.compose.runtime.getValue
import androidx.compose.runtime.mutableStateOf
import androidx.compose.runtime.remember
import androidx.compose.ui.Modifier
import androidx.compose.ui.layout.ContentScale
import androidx.compose.ui.res.painterResource
import androidx.compose.ui.semantics.Role.Companion.Image
import androidx.compose.ui.text.font.FontWeight
import androidx.compose.ui.tooling.preview.Preview
import androidx.compose.ui.unit.dp
import androidx.compose.ui.unit.sp
import app.risqiikhsani.ui.theme.CobacobaTheme


class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            CobacobaTheme {
                // A surface container using the 'background' color from the theme
                Surface(
                    modifier = Modifier.fillMaxSize(),
                    color = MaterialTheme.colors.background
                ) {
                    MyApp()
                }
            }
        }
    }
}

data class Item(
    val image: Int,
    val title: String,
    val text: String
)

@Composable
fun MyApp() {
    val items = remember { generateItems() }
    var currentIndex by remember { mutableStateOf(0) }

    Column(
        modifier = Modifier
            .fillMaxSize()
            .padding(16.dp)
    ) {
        Image(
            painter = painterResource(id = items[currentIndex].image),
            contentDescription = null,
            contentScale = ContentScale.Crop,
            modifier = Modifier
                .fillMaxWidth()
                .height(200.dp)
        )
        Spacer(modifier = Modifier.height(16.dp))
        Text(
            text = items[currentIndex].title,
            fontSize = 20.sp,
            fontWeight = FontWeight.Bold
        )
        Spacer(modifier = Modifier.height(8.dp))
        Text(
            text = items[currentIndex].text,
            fontSize = 16.sp,
        )
        Spacer(modifier = Modifier.weight(1f))
        Row(
            modifier = Modifier
                .fillMaxWidth()
                .padding(vertical = 16.dp),
            horizontalArrangement = Arrangement.SpaceBetween,
        ) {
            Button(
                onClick = {
                    currentIndex = (currentIndex - 1 + items.size) % items.size
                },
                enabled = currentIndex > 0,
            ) {
                Text("Previous")
            }

            Button(
                onClick = {
                    currentIndex = (currentIndex + 1) % items.size
                },
                enabled = currentIndex < items.size - 1,
            ) {
                Text("Next")
            }
        }
    }
}

@Composable
fun generateItems(): List<Item> {
    val item1 = Item(image = R.drawable.image1, title = "Title 1", text = "Text 1")
    val item2 = Item(image = R.drawable.image2, title = "Title 2", text = "Text 2")
    val item3 = Item(image = R.drawable.image3, title = "Title 3", text = "Text 3")
    val item4 = Item(image = R.drawable.image4, title = "Title 4", text = "Text 4")
    val item5 = Item(image = R.drawable.image5, title = "Title 5", text = "Text 5")
    val item6 = Item(image = R.drawable.image6, title = "Title 6", text = "Text 6")
    val item7 = Item(image = R.drawable.image7, title = "Title 7", text = "Text 7")
    val item8 = Item(image = R.drawable.image8, title = "Title 8", text = "Text 8")
    val item9 = Item(image = R.drawable.image9, title = "Title 9", text = "Text 9")
    val item10 = Item(image = R.drawable.image10, title = "Title 10", text = "Text 10")

    return listOf(item1, item2, item3, item4, item5, item6, item7, item8, item9, item10)
}

@Preview(showBackground = true)
@Composable
fun DefaultPreview() {
    CobacobaTheme {

    }
}
