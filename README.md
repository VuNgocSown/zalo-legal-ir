# Zalo Legal Information Retrieval
Dự án Zalo Legal IR.

## Cấu trúc thư mục

Dự án được tổ chức theo cấu trúc sau:

```text
zalo-legal-ir/
│
├── data/                          # Không push lên Git (đã thêm vào .gitignore)
│   ├── corpus.jsonl
│   ├── queries.jsonl
│   └── qrels.tsv
│
├── embeddings/                    # Không push lên Git (file nặng)
│   └── corpus_vectors.npy
│
├── src/
│   ├── base/                      # Sơn làm riêng
│   │   ├── load_data.py           # Load + tiền xử lý dataset
│   │   ├── tfidf_retrieval.py     # TF-IDF baseline
│   │   ├── bm25_retrieval.py      # BM25 + tune k1, b
│   │   └── evaluate.py            # Hàm tính MRR, P@10 tự viết
│   │
│   ├── dense/                     # Nguyên làm riêng
│   │   ├── dense_retrieval.py     # Encode + FAISS search
│   │   ├── reranker.py            # Cross-Encoder rerank
│   │   └── evaluate.py            # Benchmark riêng (copy từ base)
│   │
│   └── shared/                    # Cả 2 dùng chung, KHÔNG sửa bừa
│       ├── data_loader.py         # Hàm load dataset dùng chung
│       ├── metrics.py             # MRR, P@10 chuẩn dùng chung
│       └── hybrid_rrf.py          # RRF fusion (cả 2 cùng làm)
│
├── notebooks/
│   ├── base_experiments.ipynb     # Notebook của Sơn
│   ├── dense_experiments.ipynb    # Notebook của Nguyên
│   └── final_comparison.ipynb     # Notebook tổng hợp kết quả
│
├── results/                       # Lưu kết quả chạy dưới dạng JSON/CSV
│   ├── tfidf_results.json
│   ├── bm25_results.json
│   ├── dense_results.json
│   ├── hybrid_results.json
│   └── reranker_results.json
│
├── requirements.txt
├── .gitignore
└── README.md
```
