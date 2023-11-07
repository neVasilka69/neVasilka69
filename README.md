### я не пидар👋

### [Интеллектуальные ИСИТ](https://drive.google.com/drive/folders/1jyDnf93uVqdsYxuppCK5Xx1Ahma_0zES) </br>
https://drive.google.com/drive/folders/1jyDnf93uVqdsYxuppCK5Xx1Ahma_0zES </br>
### [Статистические методы обработки информации](https://drive.google.com/drive/folders/1hQEN1Bsa194XCQ0e4lPD0Aa_dMymt0jr) </br>
https://drive.google.com/drive/folders/1hQEN1Bsa194XCQ0e4lPD0Aa_dMymt0jr </br>
### [Администрирование ИС](https://disk.yandex.ru/d/2x2bJi0B3SrBKY) </br>
https://disk.yandex.ru/d/2x2bJi0B3SrBKY

=============
from enum import Enum

class TYPE(Enum):
    AKO = "ako"
    IS_A = "is_a"
    HAS_ATTRIBUTE = "has_attribute"


class Element:
    def __init__(self, name, link_type: TYPE, elements: list):
        self.name = name
        self.type = link_type
        self.parents = elements



PORTABLE = 'портативное устройство'

TABLET = 'планшет'
SMARTPHONE = 'смартфон'

SAMSUNG = 'samsung'

DEFAULT = 'стандартный'
FOLD = 'раскладушка'

GALAXY_S9 = 'galaxy tab s9'
GALAXY_A8 = 'galaxy tab a8'

IPHONE_5S = 'iphone 5s'
SAMSUNG_GALAXY_FOLD = 'samsung galaxy fold'


def has_link(curr_element: Element, target: Element, target_link: TYPE):
    while True:
        next_element = curr_element.parents
        if next_element == target and curr_element.type == target_link:
            return True

        next_elements = curr_element.parent

        if next_elements is None:
            return False

        for next_element in next_elements:
            has_link(next_element, target, target_link)

        curr_element = next_element


def main():
    portable = Element(PORTABLE, None, None)

    tablet = Element(TABLET, TYPE.AKO, [portable])
    smartphone = Element(SMARTPHONE, TYPE.AKO, [portable])

    samsungs = Element(SAMSUNG, TYPE.AKO, [tablet])
    default_smartphone = Element(DEFAULT, TYPE.AKO, [smartphone])
    fold = Element(FOLD, TYPE.AKO, [smartphone])

    curr_element = samsungs
    target = portable
    target_link = TYPE.AKO

    result = has_link(curr_element, target, target_link)



    print(result)

main()


