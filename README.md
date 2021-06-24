[![ionproject.org](https://raw.githubusercontent.com/i-on-project/integration/master/img/i-on_logo.png)](https://www.ionproject.org)

# Introduction
The I-On initiative aims to build an extensible platform that is the reference point to the academic community, aggregating published information regarding term calendars, timetables, courses, and other items of relevance.

I-On Integration is a sub-project of the initiative and its main goal is to collect unstructured data from external sources and make the information available in a format that can be understood by other components.

This repository holds the strutured data made available by I-On Integration making it available to other I-On sub-projects.

# Data Structure

The following diagram depics the structure defined to maintain the data.

![Data Structure](https://github.com/i-on-project/integration-data/blob/master/img/I-On_Integration-Data_Structure.png)

The name of the folders for the schools will be based on the package naming prefix used by Java using the reversed Internet domain name for each institution qualified name.

Each school will have a folder `academic_years`with the several academic years containing that year's academic calendar in the format `YYYY-YYYY`. The institution will also have a folder named `programmes` containing the several programmes breaked down by calendar term (semester) in the format `YYYY-YYYY-[1|2]` where the last digit refers either to the first (`1`) or the second semester (`2`).


## Timetables

The `timetable.yml` file will be formatted as follows: 

```yml
creationDateTime: 20210421T204916Z      # Coordinated Universal Time (UTC) - ISO 8601
retrievalDateTime: 20210421T204916Z      # Coordinated Universal Time (UTC) - ISO 8601
school:
  name: "INSTITUTO SUPERIOR DE ENGENHARIA DE LISBOA"
  acr: ISEL
programme:
  name: "Licenciatura em Engenharia Informática e de Computadores"
  acr: LEIC
calendarTerm: 2020-2021-2
classes:
  -   acr: E
      sections:
        - section: LEIC11Da
          events:
            - category: LECTURE  # [LECTURE | PRACTICE | LAB | LECTURE_PRACTICE]
              location:
                - L_H2    # not mandatory
              beginTime: "14:00"
              duration: "01:30"
              weekday: MO # RFC 5545  [ SU | MO | TU | WE | TH | FR | SA ]
            - category: LECTURE
              beginTime: "14:00"
              duration: "01:30"
              weekday: WE
            - category: LECTURE
              beginTime: "14:00"
              duration: "01:30"
              weekday: TH
          instructors:
            - name: 'Teacher A'
              category: PRACTICE
            - name: 'Teacher B'
              category: LECTURE
```

## Exam Schedule

For the `exam_schedule.yaml` file will have the format:

```yml
creationDateTime: 20210421T204916Z
retrievalDateTime: 20210421T204916Z
school:
    name: Instituto Superior Engenharia Lisboa 
    acr: ISEL
programme:
    name: Licenciatura em Engenharia Informática e de Computadores
    acr: LEIC
calendarTerm: 2019-2020-2
exams:
    - name: AED
      startDate: 2020-07-09T14:00:00.000
      endDate: 2020-07-09T17:00:00.000
      category: TEST #TEST | EXAM_NORMAL | EXAM_ALTERN | EXAM_SPECIAL
      location: 
```

The formats of each key are similar to the ones used in `timetable.yml`, with the exception of `category`. This key will classify the evaluations with **one** the following values `[ TEST | EXAM_NORMAL | EXAM_ALTERN | EXAM_SPECIAL ]`.

## Academic Calendar

Finally `calendar.yml`:

```yml
creationDateTime: 20210421T204916Z
retrievalDateTime: 20210421T204916Z
school:
  name: Instituto Superior Engenharia Lisboa 
  acr: ISEL
language: pt-PT
terms:
  - calendarTerm: 2019-2020-1
    interruptions:
      - name: Férias Natal
        startDate: 2019-12-23
        endDate: 2020-01-04
    evaluations:
      - name: Exames época normal
        startDate: 2020-01-13
        endDate: 2020-02-01
        duringLectures: false
      - name: Exames época recurso
        startDate: 2020-02-03
        endDate: 2020-02-15
        duringLectures: false
      - name: Exames época especial
        startDate: 2020-02-26
        endDate: 2020-03-07
        duringLectures: true
    details:
      - name: Turmas 1º Semestre
        curricularTerm:
          - id: 1
        startDate: 2019-09-16
        endDate: 2020-01-11
      - name: Turmas excepto 1º Semestre
        curricularTerm:
          - id: 2
          - id: 3
          - id: 4
          - id: 5
          - id: 6
        startDate: 2019-09-09
        endDate: 2019-12-21
    otherEvents:
      - name: Divulgação de horários
        startDate: 2019-07-22
        endDate: 2019-07-22
      - name: Abertura das atividades letivas 2019/2020
        startDate: 2019-09-02
        endDate: 2019-09-02
      - name: Data limite para lançamento de classificações no Portal Académico (frequência, exames de época normal e de época de recurso)
        startDate: 2020-02-21
        endDate: 2020-02-21
      - name: Data limite para lançamento de classificações no Portal Académico (época especial)
        startDate: 2020-03-14
        endDate: 2020-03-14
```

A particular note to `curricularTerm` with indicates the academic semesters afected by the specific events.


# Resources
* [List of Academic Institutions in Portugal](https://www.dges.gov.pt/guias/indest.asp)
* [List of Higher Education Programmes in Portugal](https://www.dges.gov.pt/guias/indcurso.asp)