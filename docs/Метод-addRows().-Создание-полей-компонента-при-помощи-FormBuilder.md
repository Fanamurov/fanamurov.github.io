Метод addRows() используется для определение состава и логики полей компонента в админке и на фронте. В качестве хелпера используется [FormBuilder](https://github.com/Fanamurov/larrock-core/wiki/FormBuilder)

### Создание поля:

В конструкторе компонента:
    
    $this->addRows()

Определяем метод:

    protected function addRows()
    {
        $row = new FormInput('имя поля в БД', 'Название поля');
        $this->rows['имя поля в БД'] = $row->методы FBElement настройки поля;

        //other rows
        return $this;
    }