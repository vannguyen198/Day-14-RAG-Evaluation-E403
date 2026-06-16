# Day 14 — Reflection
## Evaluation Report & Failure Analysis

---

## 1. Benchmark Results Summary

Paste results từ Exercise 3.2 và tóm tắt:

**Overall pass rate:** 0%

**Average scores:**

| Metric | Average | Min | Max | Std Dev |
|--------|---------|-----|-----|---------|
| Faithfulness | 0.06926406926406926 | | | |
| Relevance | 0.08237133237133237 | | | |
| Completeness | 0.10208617746615556 | | | |
| Overall Score |  | | | |

**Score interpretation (theo bài giảng):**
- Bao nhiêu metrics ở Good (0.8–1.0)? 0
- Bao nhiêu metrics ở Needs Work (0.6–0.8)? 0
- Bao nhiêu metrics ở Significant Issues (<0.6)? 21

**Failure type distribution:**

| Failure Type | Count | Percentage |
|--------------|-------|------------|
| hallucination | 20 | 95.24% |
| irrelevant | 1 | 4.76% |
| incomplete | 0 | 0% |
| off_topic | 0 | 0% |
| refusal | 0 | 0% |
| other | 0 | 0% |

---

## 2. Top 3 Worst Failures — 5 Whys Analysis

Theo bài giảng: "Phân loại failure TRƯỚC KHI fix. Đừng fix từng failure riêng lẻ — CLUSTER rồi fix root cause."

### Failure 1

**Question:** *paste question here*

**Agent Answer:** *paste actual output*

**Scores:** Faithfulness: ___ | Relevance: ___ | Completeness: ___ | Overall: ___

**5 Whys Analysis:**
| Level | Question | Answer |
|-------|----------|--------|
| Symptom | Vấn đề là gì? | |
| Why 1 | Tại sao xảy ra? | |
| Why 2 | Tại sao Why 1 xảy ra? | |
| Why 3 | Tại sao Why 2 xảy ra? | |
| Why 4 | Root cause là gì? | |

**Root cause (from `find_root_cause()`):**
> *Output của function:*

**Bạn có đồng ý với root cause suggestion không? Tại sao?**
> *Your answer:*

**Proposed fix (cụ thể, actionable):**
> *Your answer: 1–2 actions cụ thể*

---

### Failure 2

**Question:** *paste question here*

**Agent Answer:** *paste actual output*

**Scores:** Faithfulness: ___ | Relevance: ___ | Completeness: ___ | Overall: ___

**5 Whys Analysis:**
| Level | Question | Answer |
|-------|----------|--------|
| Symptom | | |
| Why 1 | | |
| Why 2 | | |
| Why 3 | | |
| Why 4 | | |

**Root cause:**
> *Your answer:*

**Proposed fix:**
> *Your answer:*

---

### Failure 3

**Question:** *paste question here*

**Agent Answer:** *paste actual output*

**Scores:** Faithfulness: ___ | Relevance: ___ | Completeness: ___ | Overall: ___

**5 Whys Analysis:**
| Level | Question | Answer |
|-------|----------|--------|
| Symptom | | |
| Why 1 | | |
| Why 2 | | |
| Why 3 | | |
| Why 4 | | |

**Root cause:**
> *Your answer:*

**Proposed fix:**
> *Your answer:*

---

## 3. Failure Clustering

Theo bài giảng: "Fix 1 root cause giải quyết nhiều failures cùng lúc."

**Cluster Analysis:**

| Cluster | Root Cause | Failures in cluster | Priority |
|---------|-----------|--------------------:|----------|
| 1 | | | High/Medium/Low |
| 2 | | | |
| 3 | | | |

**Nếu chỉ fix 1 cluster, bạn chọn cluster nào? Tại sao?**
> *Your answer:*

---

## 4. Improvement Log (from `generate_improvement_log`)

Paste output của `generate_improvement_log()`:

```
[paste markdown table output here]
```

**Thêm 3 improvement suggestions từ `generate_improvement_suggestions()`:**
1. ___
2. ___
3. ___

---

## 5. Regression Testing Strategy

### CI/CD Integration

**Câu 1: Khi nào chạy `run_regression()` trong production system?**
> *Mô tả CI/CD integration point (ví dụ: trước mỗi merge to main, sau mỗi prompt change, etc.):*

**Câu 2: Threshold regression 0.05 có phù hợp domain của bạn không?**
> *Strict hơn hay loose hơn? Tại sao?*

**Câu 3: Khi phát hiện regression — block deployment hay chỉ alert?**
> *Your answer + giải thích trade-off:*

**Câu 4: Eval pipeline nên chạy ở đâu trong CI/CD flow?**

```
Code change → [___] → [___] → [___] → Deploy
              (bước 1)   (bước 2)   (bước 3)
```
> *Điền 3 bước eval vào flow trên:*

---

## 6. Continuous Improvement Loop

## 6. Continuous Improvement Loop

Theo bài giảng: Evaluate → Analyze → Improve → Augment (add to benchmark) → lặp lại

**Sau lab hôm nay, 3 actions tiếp theo bạn sẽ làm để improve agent:**

| Priority | Action | Metric sẽ improve | Expected impact |
| :---: | --- | --- | --- |
| **1** | **Phân tích log lỗi (Error Analysis) & tinh chỉnh Prompt:** Rà soát các ca thất bại trong lab, bổ sung Few-shot examples hoặc thêm các ràng buộc điều kiện (Constraints) vào System Prompt. | **Accuracy / Success Rate** (Tỷ lệ hoàn thành nhiệm vụ chính xác) | Giảm thiểu các lỗi logic cơ bản, định hướng agent hiểu đúng ngữ cảnh và xuất ra kết quả (output) chuẩn format ngay từ đầu. |
| **2** | **Tối ưu hóa quy trình gọi Tool (Tool-use Optimization):** Cải tiến mô tả hàm (Function description) hoặc thêm bước Validation (kiểm tra điều kiện) trước khi Agent kích hoạt tool. | **Tool Call Error Rate / Latency** (Giảm tỷ lệ gọi sai tool và thời gian xử lý) | Agent chọn đúng tool cần thiết, truyền đủ tham số chính xác và không bị lặp lại các vòng gọi tool vô hạn (looping). |
| **3** | **Xây dựng cơ chế Handle Error tự động (Fallback Mechanism):** Lập trình thêm phân đoạn bắt lỗi tự động khi Agent trả về kết quả sai hoặc Tool trả về lỗi hệ thống (như lỗi kết nối API, parsing error). | **Robustness / Resilience** (Độ bền bỉ và khả năng tự phục hồi của hệ thống) | Agent không bị crash hoặc dừng hoạt động khi gặp lỗi bất ngờ; có thể tự sửa sai hoặc đưa ra câu trả lời thay thế an toàn. |

**Bạn sẽ thêm failure cases nào vào benchmark cho sprint tiếp theo?**

1. **Case 1: Yêu cầu mơ hồ hoặc thiếu thông tin từ người dùng (Ambiguous User Input)**
   * *Mô tả:* Người dùng đưa ra yêu cầu chung chung, thiếu thông tin cốt lõi để kích hoạt Tool hoặc chứa thông tin mâu thuẫn trực tiếp.
   * *Mục tiêu đánh giá:* Kiểm tra xem Agent có biết dừng lại để hỏi làm rõ thông tin (Clarification) hay sẽ tự "suy diễn" rồi gọi sai Tool/Tham số.

2. **Case 2: Tool trả về kết quả rỗng hoặc báo lỗi hệ thống (Empty/Error Tool Response)**
   * *Mô tả:* Giả lập tình huống khi Agent gọi một Tool nhưng Tool đó trả về kết quả rỗng (No data found) hoặc báo lỗi hệ thống phía bên thứ ba (API Error).
   * *Mục tiêu đánh giá:* Đảm bảo Agent không bê nguyên mã lỗi kỹ thuật trả cho người dùng, mà biết tự xử lý thông minh (ví dụ: thử lại, tìm giải pháp thay thế, hoặc thông báo lịch sự).

3. **Case 3: Chuỗi ràng buộc phức tạp gồm nhiều bước (Multi-constraint / Multi-step Reasoning)**
   * *Mô tả:* Một yêu cầu đòi hỏi Agent phải thực hiện từ 3 bước logic trở lên theo một thứ tự nghiêm ngặt (Ví dụ: "Tìm thông tin X, dùng X để tính toán ra Y, sau đó định dạng Y thành bảng và chỉ giữ lại top 3").
   * *Mục tiêu đánh giá:* Đánh giá khả năng bám sát kế hoạch hành động (Planning) và độ ổn định của Agent qua các chuỗi suy nghĩ dài (Long-horizon tasks).

---

## 7. Framework Reflection

**Framework bạn đã dùng trong lab:** RAGAS (RAGAS-inspired heuristic)
Test thất bại do phiên bản 0.4.3 không tương thích. Ở các phiên bản từ `0.4.x` trở đi, cấu trúc trả về của hàm `evaluate()` đã được tái cấu trúc hoàn toàn từ phía backend. Thư viện không còn hỗ trợ các phương thức truy xuất dữ liệu theo dạng mảng (`list`) hoặc `dict` truyền thống, mà bắt buộc quản lý nghiêm ngặt qua đối tượng `Result` (dựa trên nền tảng **Pydantic v2** và tích hợp sâu với **Pandas DataFrame**). Điều này dẫn đến việc các hàm tự định nghĩa của hệ thống cũ như `runner.identify_failures()` hoặc bộ phân tích `FailureAnalyzer` bị gãy logic do không đồng bộ kiểu dữ liệu (gây ra lỗi `AttributeError` hoặc `ValidationError`). Production cực kỳ sợ việc tự động update thư viện làm sập hệ thống (như case 0.4.3). Khi dùng Ragas ở production, bắt buộc phải pin cứng version của cả Ragas, Pydantic và LangChain.

**Nếu dùng trong production, bạn sẽ chọn framework nào? Tại sao?**
> *Tham khảo trade-offs table trong bài giảng:*

**Nếu dùng trong production, bạn sẽ chọn framework nào? Tại sao?**
> *Lựa chọn đề xuất: **Ragas** (Được đóng băng phiên bản ổn định và kết hợp với nền tảng Tracking như **Phoenix** hoặc **LangSmith**)*

| Tiêu chí | Lý do chọn |
| :--- | :--- |
| **Focus phù hợp vì...** | Ragas tập trung rất mạnh vào **End-to-End RAG Metrics** (như Faithfulness, Answer Relevancy, Context Recall) bằng phương pháp *LLM-as-a-judge*. Trong môi trường production, việc kiểm soát hiện tượng "ảo tưởng" (hallucination) là ưu tiên số một. Ragas cung cấp các công cụ định lượng chính xác các chỉ số này dựa trên dữ liệu thực tế thay vì chỉ đánh giá cảm tính. |
| **CI/CD integration vì...** | Khi kết hợp cấu hình Ragas chạy qua các bộ công cụ như GitHub Actions hoặc Promptfoo, bộ Benchmark sẽ biến thành một bước **Integration Test** bắt buộc trước khi deploy. Bản chất dữ liệu đầu ra của Ragas dạng Pandas DataFrame giúp dễ dàng viết script tự động để chặn lệnh triển khai (Block Deployment) nếu điểm trung bình của hệ thống thấp hơn ngưỡng an toàn (ví dụ: `threshold < 0.7`). |
| **Team workflow vì...** | Khi tích hợp Ragas vào một Dashboard theo dõi (như Arize Phoenix hoặc Langfuse), workflow của team được phân tách rõ ràng: Kỹ sư lập trình tập trung tối ưu Agent, trong khi Data Scientist hoặc bộ phận QA có thể trực tiếp theo dõi biểu đồ trực quan, phân cụm lỗi (Cluster failures) và bổ sung các ca thất bại thực tế từ người dùng vào bộ test chuẩn (bước *Augment*) mà không làm ảnh hưởng đến mã nguồn chính. |