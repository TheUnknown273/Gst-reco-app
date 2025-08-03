# Gst-reco-app
from kivy.app import App
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.button import Button
from kivy.uix.label import Label
from kivy.uix.filechooser import FileChooserIconView
import os

class GSTApp(App):
    def build(self):
        layout = BoxLayout(orientation='vertical', spacing=10, padding=10)

        self.label = Label(text='Select a file to clean (Dummy for now)', size_hint_y=0.2)
        self.chooser = FileChooserIconView()
        self.button = Button(text='Clean File', size_hint_y=0.2)
        self.button.bind(on_press=self.dummy_clean)

        layout.add_widget(self.label)
        layout.add_widget(self.chooser)
        layout.add_widget(self.button)
        return layout

    def dummy_clean(self, instance):
        if self.chooser.selection:
            file_path = self.chooser.selection[0]
            self.label.text = f"✅ Cleaned: {os.path.basename(file_path)}"
        else:
            self.label.text = "❌ Please select a file first"

GSTApp().run()
