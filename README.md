# Tối ưu siêu tham số bằng PSO cải tiến

Đồ án nghiên cứu Particle Swarm Optimization (PSO) và biến thể AIW-PSO cho bài toán tối ưu siêu tham số mô hình học máy. Các thí nghiệm so sánh Default, Grid Search, Random Search, PSO và AIW-PSO trên XGBoost và SVM.

## Cấu trúc

- `notebooks/XGB.ipynb`: thực nghiệm với XGBoost.
- `notebooks/SVM.ipynb`: thực nghiệm với SVM.
- `data/`: CSV dự phòng cho Letter Recognition và Breast Cancer Wisconsin.
- `results/summary.csv`: bảng tổng hợp Loss, Accuracy (%) và thời gian chạy.
- `requirements.txt`: các thư viện Python cần thiết.

## Thuật toán

AIW-PSO kết hợp trọng số quán tính thích nghi, hệ số gia tốc biến thiên theo thời gian (TVAC) và cơ chế tái khởi tạo một phần quần thể khi quá trình tìm kiếm bị trì trệ.

## Dữ liệu

Notebook tải Letter Recognition từ OpenML bằng `fetch_openml("letter", version=1)`. Breast Cancer Wisconsin được tải từ bộ dữ liệu tích hợp trong scikit-learn. Các file trong `data/` là bản dự phòng để dùng khi không thể tải dữ liệu trực tuyến.

## Nếu không tải được dữ liệu trực tuyến

Không cần chỉnh sửa file notebook. Nếu cell tải Letter Recognition từ OpenML bị lỗi, bỏ qua cell đó và chạy một cell mới với đoạn sau:

```python
import pandas as pd
from sklearn.preprocessing import LabelEncoder

df = pd.read_csv("../data/letter_recognition.csv")
x = df.drop(columns="target").to_numpy()
y = LabelEncoder().fit_transform(df["target"].astype(str))
```

Đoạn này tạo lại hai biến `x` và `y` mà các cell thí nghiệm sử dụng. File có 20.000 dòng, 16 đặc trưng và cột nhãn `target`.

Nếu không tải được Breast Cancer Wisconsin từ scikit-learn, bỏ qua cell tải dữ liệu tương ứng và chạy cell mới:

```python
import pandas as pd

df = pd.read_csv("../data/breast_cancer.csv")
x = df.drop(columns="target").to_numpy()
y = df["target"].to_numpy()
```

File có 569 dòng, 30 đặc trưng và cột nhãn `target`.

Các đường dẫn trên giả định notebook được mở từ thư mục `notebooks/` trong repository. Nếu môi trường notebook dùng thư mục làm việc khác, điều chỉnh đường dẫn tương đối tới thư mục `data/`.

## Cài đặt

```bash
pip install -r requirements.txt
```

## Chạy notebook

Mở notebook trong Kaggle hoặc Jupyter Notebook và chạy các cell theo thứ tự. Các lượt PSO trên Letter Recognition có thể mất nhiều thời gian. Thời gian trong bảng kết quả là thời gian của các lần chạy trên Kaggle và phụ thuộc cấu hình máy.

## Kết quả

Xem toàn bộ kết quả tại [results/summary.csv](results/summary.csv). Thời gian chạy không nên so sánh giữa các máy có cấu hình khác nhau.
