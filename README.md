# Tối ưu siêu tham số bằng PSO cải tiến

Đồ án nghiên cứu Particle Swarm Optimization (PSO) và biến thể AIW-PSO trong bài toán tối ưu siêu tham số cho mô hình học máy. Thực nghiệm so sánh các phương pháp tìm kiếm trên XGBoost và SVM với hai bộ dữ liệu Breast Cancer Wisconsin và Letter Recognition.

## Nội dung

- `notebooks/SVM.ipynb`: thực nghiệm PSO, AIW-PSO, Grid Search và Random Search với SVM.
- `results/summary.csv`: bảng tổng hợp Loss, Accuracy và thời gian chạy của các kết quả đã ghi nhận. Notebook XGBoost sẽ được bổ sung sau.
- `requirements.txt`: các thư viện Python cần thiết.

## Thuật toán

AIW-PSO kết hợp trọng số quán tính thích nghi, hệ số gia tốc biến thiên theo thời gian (TVAC) và cơ chế tái khởi tạo một phần quần thể khi quá trình tìm kiếm bị trì trệ.

## Dữ liệu

- Breast Cancer Wisconsin: tải từ bộ dữ liệu tích hợp trong scikit-learn.
- Letter Recognition: tải bằng `fetch_openml("letter", version=1)`.

Không lưu bản sao dữ liệu trong repository. Lần chạy Letter Recognition cần kết nối Internet để tải dữ liệu từ OpenML.

## Cài đặt

```bash
pip install -r requirements.txt
```

## Chạy notebook

Mở `notebooks/SVM.ipynb` trong Kaggle hoặc Jupyter Notebook và chạy các cell theo thứ tự. PSO và AIW-PSO trên Letter Recognition có thể chạy lâu; thời gian trong `summary.csv` phụ thuộc môi trường thực nghiệm.

## Kết quả

Bảng đầy đủ nằm trong [results/summary.csv](results/summary.csv). Accuracy trong CSV được biểu diễn theo phần trăm; thời gian tính bằng giây. Các kết quả hiện có được chạy trên Kaggle.

## Ghi chú

Đây là kết quả thực nghiệm học thuật trên hai mô hình và hai bộ dữ liệu; thời gian chạy không nên so sánh giữa các cấu hình phần cứng khác nhau.
