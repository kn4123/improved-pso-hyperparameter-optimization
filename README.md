# Tối ưu siêu tham số bằng PSO cải tiến

Đồ án nghiên cứu Particle Swarm Optimization (PSO) và biến thể AIW-PSO cho bài toán tối ưu siêu tham số mô hình học máy. Các thí nghiệm so sánh Default, Grid Search, Random Search, PSO và AIW-PSO trên XGBoost và SVM.

## Cấu trúc

- `notebooks/SVM.ipynb`: thí nghiệm với SVM.
- `notebooks/XGB.ipynb`: thí nghiệm với XGBoost (sẽ được thêm sau khi xác nhận đúng bản notebook).
- `data/`: CSV cho Letter Recognition và Breast Cancer Wisconsin, dùng làm bản dữ liệu dự phòng.
- `results/summary.csv`: bảng tổng hợp Loss, Accuracy (%) và thời gian chạy.
- `requirements.txt`: thư viện Python cần thiết.

## Thuật toán

AIW-PSO kết hợp trọng số quán tính thích nghi, hệ số gia tốc biến thiên theo thời gian (TVAC) và cơ chế tái khởi tạo một phần quần thể khi quá trình tìm kiếm bị trì trệ.

## Dữ liệu và cách tải dự phòng

Notebook có thể tải Letter Recognition từ OpenML. Nếu `fetch_openml("letter", version=1)` không tải được do mạng hoặc OpenML tạm thời không truy cập được, dùng file dự phòng trong `data/letter_recognition.csv`.

Mở notebook từ thư mục `notebooks/` trong repo rồi thay cell tải Letter Recognition bằng:

```python
import pandas as pd
from sklearn.preprocessing import LabelEncoder

df = pd.read_csv("../data/letter_recognition.csv")
x = df.drop(columns="target").to_numpy()
y = LabelEncoder().fit_transform(df["target"].astype(str))
```

File có 20.000 dòng dữ liệu, 16 đặc trưng và cột nhãn `target`.

Breast Cancer Wisconsin được tải từ scikit-learn. Nếu môi trường không tải được hoặc muốn dùng bản CSV kèm repo, thay cell tải dữ liệu bằng:

```python
import pandas as pd

df = pd.read_csv("../data/breast_cancer.csv")
x = df.drop(columns="target").to_numpy()
y = df["target"].to_numpy()
```

File có 569 dòng, 30 đặc trưng và cột nhãn `target`.

## Cài đặt

```bash
pip install -r requirements.txt
```

## Chạy notebook

Mở notebook trong Kaggle hoặc Jupyter Notebook và chạy các cell theo thứ tự. Các lượt PSO trên Letter Recognition có thể mất nhiều thời gian. Thời gian trong bảng kết quả là thời gian của các lần chạy trên Kaggle và phụ thuộc cấu hình máy.

## Kết quả

Xem toàn bộ kết quả tại [results/summary.csv](results/summary.csv). Các số liệu là kết quả thực nghiệm đã ghi nhận; không nên so sánh thời gian giữa các máy có cấu hình khác nhau.

