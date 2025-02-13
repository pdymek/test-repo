# test_repo
test1cg



































\\





























import os
import numpy as np
import math

BASE_DIR = os.path.dirname(os.path.abspath(__file__))


class Solution:
    def __init__(self, task_name: str):
        self.task_name = task_name
        self.misc_init()
        self.load_file()
        self.get_result()
        # self.save_result()

    def misc_init(self):
        self.input_path = f"{BASE_DIR}/../inputs/level2_{self.task_name}.in"
        self.output_path = f"{BASE_DIR}/../my_outputs/level2_{self.task_name}.out"

        if os.path.exists(self.output_path):
            os.remove(self.output_path)

        self.raw_data = []
        self.data = []

    def load_file(self):
        with open(self.input_path, "r") as input_file:
            for n, file_line in enumerate(input_file):
                if n == 0:
                    self.size = [int(a) for a in file_line.split(" ")]
                else:
                    self.raw_data.append([int(a) for a in file_line.split(" ")])
        
        # self.data = np.array(self.raw_data)
        for n, line in enumerate(self.raw_data):
            self.data.append(line[1::2])

        self.arr = np.array(self.data)
    
    def get_result(self):
        # self.result = f"{np.min(self.data)} {np.max(self.data)} {math.floor(np.mean(self.data))}"
        self.result = {}
        for country in range(0, np.max(self.arr+1)):
            if country not in self.result:
                self.result[country] = 0
        check_coords = [[1, 0], [0, 1], [-1, 0], [0, -1]]

        for y, line in enumerate(self.arr):
            for x, val in enumerate(line):
                if y == 0 or x == 0 or y == len(self.arr)-1 or x == len(line)-1:
                    self.result[val] += 1
                
                else:
                    is_border = False
                    for nc, check_coord in enumerate(check_coords):
                        if self.arr[y+check_coord[1]][x+check_coord[0]] != val:
                            is_border= True
                            break
                    
                    if is_border:
                        self.result[val] += 1


    def save_result(self):
        with open(self.output_path, "a+") as output_file:
            output_file.write(self.result + "\n")


if __name__ == "__main__":
    # solution = Solution("1")
    # solution = Solution("2")
    solution = Solution("example")
    print("done")



















\















'










































import math
rules = [
    1,
    [4, 2],
    [1, 1, 1],
    [2, 2, 2],
    1,
    2,
    3,
    4,
]

class rule:
    def __init__(self, rules):
        self.rules = rules
        self.no_of_test_cases = rules[0]
        self.test_case_controls = rules[1]
        self.no_of_boxes = rules[1][1]
        self.no_of_sticks = rules[1][0]
        self._get_boxes()
        self._get_sticks()

    def _get_boxes(self):
        start_position = 2
        stop_position = start_position + self.no_of_boxes
        self.boxes = self.rules[start_position:stop_position]

    def _get_sticks(self):
        start_position = 2 + self.no_of_boxes
        stop_position = start_position + self.no_of_sticks
        self.sticks = self.rules[start_position:stop_position]
        

class solution:
    def __init__(self, rules):
        self.rules = rule(rules)

    def run(self):
        self.set_diagonals()
        for stick in self.rules.sticks:
            stick_status = False
            for box_key, box in self.rules.boxes_with_diagonals.items():
                if stick <= box['diagonal']:
                    stick_status = True
                
                if stick_status == True:
                    break

            print(stick_status)
            
    
    def set_diagonals(self):
       boxes_with_diagonals = {}
       for i, box_dims in enumerate(self.rules.boxes):
            boxes_with_diagonals[i] = {
                'dims': box_dims,
                'diagonal': self.calculate_diagonal(box_dims)
            }
       self.rules.boxes_with_diagonals = boxes_with_diagonals        
       
    @staticmethod
    def calculate_diagonal(cuboid_dims: list[int]) -> float:
        return math.sqrt(sum([dim**2 for dim in cuboid_dims]))



if __name__ == "__main__":
    solution_task = solution(rules)
    solution_task.run()
    print('ast')








    









x












\




z





\
































sf




















































































