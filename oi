class Student:
    def __init__(self, student_id, name, theory_score, practice_score, assignment_score):
        self.id = student_id
        self.name = name
        self.theory_score = theory_score
        self.practice_score = practice_score
        self.assignment_score = assignment_score

        self.average_score = 0
        self.academic_type = ""

        self.calculate_average()
        self.classify_academic()

    def calculate_average(self):
        self.average_score = round(
            self.theory_score * 0.4
            + self.practice_score * 0.4
            + self.assignment_score * 0.2,
            2
        )

    def classify_academic(self):

        if self.average_score < 5:
            self.academic_type = "Yếu"
        elif self.average_score < 6.5:
            self.academic_type = "Trung bình"
        elif self.average_score < 8:
            self.academic_type = "Khá"
        else:
            self.academic_type = "Giỏi"


class StudentManager:
    def __init__(self):
        self.students = []

    def show_all(self):
        if not self.students:
            print("Danh sách sinh viên đang rỗng!")
            return

        print(
            f"{'Mã SV':<12}"
            f"{'Họ tên':<25}"
            f"{'LT':<8}"
            f"{'TH':<8}"
            f"{'BT':<8}"
            f"{'Tổng kết':<12}"
            f"{'Học lực'}"
        )

        for student in self.students:
            print(
                f"{student.id:<12}"
                f"{student.name:<25}"
                f"{student.theory_score:<8}"
                f"{student.practice_score:<8}"
                f"{student.assignment_score:<8}"
                f"{student.average_score:<12}"
                f"{student.academic_type}"
            )

    def add_student(self):
        while True:
            student_id = input("Nhập mã sinh viên: ").strip()

            if not student_id:
                print("Mã sinh viên không được rỗng!")
                continue

            is_exist = False

            for student in self.students:
                if student.id == student_id:
                    is_exist = True
                    break

            if is_exist:
                print("Mã sinh viên đã tồn tại!")
                continue

            break

        while True:
            name = input("Nhập họ tên sinh viên: ").strip()

            if not name:
                print("Họ tên không được rỗng!")
                continue

            break

        theory_score = input_score("Nhập điểm lý thuyết: ")
        practice_score = input_score("Nhập điểm thực hành: ")
        assignment_score = input_score("Nhập điểm bài tập: ")

        student = Student(
            student_id,
            name,
            theory_score,
            practice_score,
            assignment_score
        )

        self.students.append(student)

        print("Thêm sinh viên thành công!")

    def update_student(self):
        student_id = input("Nhập mã sinh viên cần cập nhật: ").strip()

        for student in self.students:
            if student.id == student_id:
                student.theory_score = input_score(
                    "Nhập điểm lý thuyết mới: "
                )
                student.practice_score = input_score(
                    "Nhập điểm thực hành mới: "
                )
                student.assignment_score = input_score(
                    "Nhập điểm bài tập mới: "
                )

                student.calculate_average()
                student.classify_academic()

                print("Cập nhật điểm sinh viên thành công!")
                return

        print("Không tìm thấy sinh viên cần cập nhật!")

    def delete_student(self):
        student_id = input("Nhập mã sinh viên cần xóa: ").strip()

        for student in self.students:
            if student.id == student_id:
                confirm = input(
                    "Bạn có chắc muốn xóa sinh viên này không? (Y/N): "
                )

                if confirm.lower() == "y":
                    self.students.remove(student)
                    print("Xóa sinh viên thành công!")

                elif confirm.lower() == "n":
                    print("Đã hủy thao tác xóa!")

                else:
                    print("Lựa chọn không hợp lệ!")

                return

        print("Không tìm thấy sinh viên cần xóa!")

    def search_student(self):
        keyword = input("Nhập từ khóa tìm kiếm: ").strip().lower()

        result = []

        for student in self.students:
            if keyword in student.name.lower():
                result.append(student)

        if not result:
            print("Không tìm thấy sinh viên phù hợp!")
            return

        print(
            f"{'Mã SV':<12}"
            f"{'Họ tên':<25}"
            f"{'Tổng kết':<12}"
            f"{'Học lực'}"
        )

        for student in result:
            print(
                f"{student.id:<12}"
                f"{student.name:<25}"
                f"{student.average_score:<12}"
                f"{student.academic_type}"
            )


def input_score(message):
    while True:
        try:
            score = float(input(message))

            if 0 <= score <= 10:
                return score

            print("Điểm phải nằm trong khoảng từ 0 đến 10!")

        except ValueError:
            print("Điểm phải là số hợp lệ!")


def show_menu():
    print("\n================ MENU ================")
    print("1. Hiển thị danh sách sinh viên")
    print("2. Thêm sinh viên mới")
    print("3. Cập nhật điểm sinh viên")
    print("4. Xóa sinh viên")
    print("5. Tìm kiếm sinh viên")
    print("6. Thoát")
    print("======================================")


def main():
    manager = StudentManager()

    while True:
        show_menu()

        choice = input("Nhập lựa chọn của bạn: ")

        match choice:
            case "1":
                manager.show_all()

            case "2":
                manager.add_student()

            case "3":
                manager.update_student()

            case "4":
                manager.delete_student()

            case "5":
                manager.search_student()

            case "6":
                print("Cảm ơn bạn đã sử dụng hệ thống quản lý sinh viên!")
                break

            case _:
                print("Lựa chọn không hợp lệ!")


if __name__ == "__main__":
    main()
