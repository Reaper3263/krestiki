def printing():
    for i in field:
        print(*i)
def write(val):
    val = list(val)
    global bol
    if int(val[0])<4 and int(val[1])<4 and field[int(val[0])][int(val[1])] == " ":
        if bol == True:
            field[int(val[0])][int(val[1])] = "X"
            bol = False
        else:
            field[int(val[0])][int(val[1])] = "0"
            bol = True
    printing()
def check():
    if any([field[1][1] == field[1][2] == field[1][3] == "X" != " ",
           field[2][1] == field[2][2] == field[2][3] == "X" != " ",
           field[3][1] == field[3][2] == field[3][3] == "X" != " ",
           field[1][1] == field[2][1] == field[3][1] == "X" != " ",
           field[1][2] == field[2][2] == field[3][2] == "X" != " ",
           field[1][3] == field[2][3] == field[3][3] == "X" != " ",
           field[1][1] == field[2][2] == field[3][3] == "X" != " ",
           field[1][3] == field[2][2] == field[3][1] == "X" != " ",]):
        return "Победил Х"
    if any([field[1][1] == field[1][2] == field[1][3] == "0" != " ",
           field[2][1] == field[2][2] == field[2][3] == "0" != " ",
           field[3][1] == field[3][2] == field[3][3] == "0" != " ",
           field[1][1] == field[2][1] == field[3][1] == "0" != " ",
           field[1][2] == field[2][2] == field[3][2] == "0" != " ",
           field[1][3] == field[2][3] == field[3][3] == "0" != " ",
           field[1][1] == field[2][2] == field[3][3] == "0" != " ",
           field[1][3] == field[2][2] == field[3][1] == "0" != " ",]):
        return "Победил 0"
    bol = False
    for i in field[1:]:
        if " " in i:
            bol = True
    if bol == False: return "Ничья"
    return "Продолжаем"

field = [[" ",1,2,3],[1," "," "," "],[2," "," "," "],[3," "," "," "]]
bol = False
print("\nНеобходимо ввести координаты выбранного поля в формате двух цифр \n1 число строка, 2 столбец\n")
printing()
while check() == "Продолжаем":
    if bol == True:
        print("\nХодит X")
    else:print("\nХодит 0")
    write(input("Введите координаты: "))
print(check())