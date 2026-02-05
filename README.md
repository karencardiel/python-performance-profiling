# <img src="https://slackmojis.com/emojis/37851-dog-computer/download" width="50"/> Python Performance Profiling

This project applies profiling techniques described in Chapter 2 to analyze Python performance in two different scenarios:

## 🔷 Section 2.1 – I/O-Bound Program

A weather data processing script that:
- Downloads CSV data from NOAA
- Stores it locally (disk cache)
- Reads files
- Computes minimum temperatures

Profiling showed the program is I/O-bound (network + disk operations dominate runtime).

## 🔷 Section 2.2 – CPU-Bound Program

A distance computation script using trigonometric operations. Profiling was done with:
- cProfile
- SnakeViz
- line_profiler

Line profiling revealed that most execution time is spent in mathematical operations (`sin`, `cos`, `atan2`, `sqrt`).

---

## 🔹 Tools Used

- `cProfile`
- `SnakeViz`
- `line_profiler`

---

## 🔹 How to Run

> **Note for Mac users:** Add `3` to all `python` commands (e.g., `python3` instead of `python`)

### 🔸 Install dependencies
```bash
pip install -r requirements.txt
```

### 🔸 Section 2.1 (I/O profiling)
```bash
python -m cProfile -s cumulative load.py 01044099999,02293099999 2021 2021 > profile.txt
```

### 🔸 Section 2.2 (CPU profiling)
```bash
python -m cProfile -o distance_cache.prof distance_cache.py
python -m snakeviz distance_cache.prof
```

**Line profiling:**
```bash
python -m kernprof -l lprofile_distance_cache.py
python -m line_profiler lprofile_distance_cache.py.lprof
```

---

## 🔹 Evidence

Screenshots and results are included in the `report/` folder.
