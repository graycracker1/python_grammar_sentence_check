from tkinter import *
import language_tool_python

root = Tk()
tool=language_tool_python.LanguageTool('en-US')
root.geometry("1160x710")

def check_grammar():
    sentence = entry.get()
    matches = tool.check(sentence)
    errors = [str(match) for match in matches]
    error_text = "\n".join(errors)
    textbox.configure(state="normal")
    textbox.insert("1.0", error_text + "\n" + "-"*91 +"\n""\n")
    textbox.configure(state="disabled")

    suggestion=[]
    for match in matches:
        if len(match.replacements)>0:
            suggestion.extend(match.replacements)
    suggestion_text="Corrected Words: " + ", ".join(suggestion)

    corrected = tool.correct(sentence)
    textbox1.configure(state='normal')
    textbox1.insert("1.0", suggestion_text + "\n" + "Possible Output: " + corrected + "\n" + "-"*91 +"\n")
    textbox1.configure(state='disabled')

def delete_first_textbox():
    textbox.configure(state="normal")
    textbox.delete(1.0, END)
    textbox.configure(state="disabled")

def delete_second_textbox():
    textbox1.configure(state="normal")
    textbox1.delete(1.0, END)
    textbox1.configure(state="disabled")

def delete_entry():
    entry.delete(0, END)

label = Label(root, text="Enter a sentence:", font=("Helvetica", 20), bg="deepskyblue1")
label.place(x=470,y=10)

entry = Entry(root, font=("Helvetica", 20))
entry.place(x=430,y=60)

button = Button(root, text="Clear Entry", command=delete_entry, font=("Helvetica", 13), bg="lightgreen")
button.place(x=750,y=62)

button1 = Button(root, text="Check Grammar", command=check_grammar, font=("Helvetica", 14), bg="lightgreen")
button1.place(x=500,y=120)


button2 = Button(root, text="Clear First Textbox", command=delete_first_textbox, font=("Helvetica", 14), bg="lightgreen")
button2.place(x=150,y=120)


textbox = Text(root, font=("Helvetica", 14), bg="#FF7D40",width=50,height=15, state=DISABLED)
textbox.place(x=8,y=170)

label1 = Label(root, text="Suggestion", font=("Helvetica", 20), bg="deepskyblue1")
label1.place(x=185,y=515)

button3 = Button(root, text="Clear Second Textbox", command=delete_second_textbox, font=("Helvetica", 14), bg="lightgreen")
button3.place(x=800,y=120)

textbox1 = Text(root, font=("Helvetica", 14), bg="#FF7D40", width=50,height=15, state=DISABLED)
textbox1.place(x=600,y=170)

label2 = Label(root, text="Corrected Output", font=("Helvetica", 20), bg="deepskyblue1")
label2.place(x=775,y=515)

root.configure(bg="deepskyblue1")

root.mainloop()
