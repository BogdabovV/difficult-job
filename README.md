
def draw_square(size, symbol):
    for i in range(size):
        for j in range(size):
            if i == 0 or i == size - 1 or j == 0 or j == size - 1:
                print(symbol, end="")
            else:
                print(" ", end="")
        print()


def draw_triangle(size, symbol):
    for i in range(size):
        for j in range(2 * size - 1):
            if (j == size - 1 - i or j == size - 1 + i) or (i == size - 1 and j > size - 1 - i and j < size - 1 + i):
                print(symbol, end="")
            else:
                print(" ", end="")
        print()


def draw_rhombus(size, symbol):
    n = size
    for i in range(n):
        for j in range(n * 2 - 1):
            if j == n - 1 - i or j == n - 1 + i:
                print(symbol, end="")
            else:
                print(" ", end="")
        print()
    for i in range(n - 2, -1, -1):
        for j in range(n * 2 - 1):
            if j == n - 1 - i or j == n - 1 + i:
                print(symbol, end="")
            else:
                print(" ", end="")
        print()


def draw_circle(radius, symbol):
    # Рисуем приблизительный круг с полым центром
    for i in range((radius * 2) + 1):
        for j in range((radius * 2) + 1):
            dist = ((i - radius) ** 2 + (j - radius) ** 2) ** 0.5
            if radius - 0.5 <= dist <= radius + 0.5:
                print(symbol, end="")
            else:
                print(" ", end="")
        print()


def draw_heart(size, symbol):
    # Размер — высота сердца
    if size < 7:
        size = 7
    width = size
    height = size

    total_width = width * 2 + 1
    matrix = [[" " for _ in range(total_width)] for _ in range(height)]

    middle_left = width // 2
    middle_right = middle_left + width + 1

    pos_left = middle_left
    pos_right = middle_right

    for i in range(height):
        for j in range(width):
            if i == 0 and middle_left - 1 <= j <= middle_left + 1:
                matrix[i][j] = symbol
            elif (i == 1 and (j == middle_left - 2 or j == middle_left + 2)) or (i == 2 and j == middle_left + 2):
                matrix[i][j] = symbol
            elif i > 2 and i < height - 1 and j == pos_left:
                matrix[i][j] = symbol
        if i >= 2:
            pos_left -= 1

    for i in range(height):
        for j in range(width):
            abs_j = middle_right + j - width
            if i == 0 and middle_left - 1 <= j <= middle_left + 1:
                matrix[i][abs_j] = symbol
            elif (i == 1 and (j == middle_left - 2 or j == middle_left + 2)) or (i == 2 and j == middle_left - 2):
                matrix[i][abs_j] = symbol
            elif i > 2 and i < height - 1 and abs_j == pos_right:
                matrix[i][abs_j] = symbol
        if i >= 2:
            pos_right += 1

    for row in matrix:
        print("".join(row))


def main():
    print("Выберите фигуру для рисования:")
    print("1 - Сердце")
    print("2 - Квадрат")
    print("3 - Круг")
    print("4 - Треугольник")
    print("5 - Ромб")

    choice = input("Введите номер фигуры: ")
    symbol = input("Введите символ для рисования фигуры: ")
    size = int(input("Введите размер фигуры (целое число не больше 3): "))
    if size < 3:
        size = 3

    if choice == "1":
        draw_heart(size, symbol)
    elif choice == "2":
        draw_square(size, symbol)
    elif choice == "3":
        draw_circle(size, symbol)
    elif choice == "4":
        draw_triangle(size, symbol)
    elif choice == "5":
        draw_rhombus(size, symbol)
    else:
        print("Неверный выбор.")


if __name__ == "__main__":
    main()ading work.py…]()
