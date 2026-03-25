# pangolinfo-amazon-scraper — Terminal 教程

> Amazon 商品数据采集技能 | 支持全球 13 个站点 | 查询 1 积分/次 | 评论 5 积分/页

---

### 1. 挂载安装与 API 认证

```bash
user@openclaw:~$ export PANGOLIN_API_KEY="pgl_a1b2c3d4exxx"

user@openclaw:~$ python3 -m clawhub install pangolinfo-amazon-scraper

  ✓ Skill installed → ~/.openclaw/skills/pangolinfo-amazon-scraper
```

### 2. 商品详情查询（ASIN → 价格/库存/详情）

```bash
user@openclaw:~$ python3 scripts/pangolin.py --asin B0DYTF8L2W --site amz_us

  > [Pangolin API] Fetching product detail for B0DYTF8L2W...
  > [Parser: amzProductDetail] Extracting 37+ fields...

  {
    "success": true,
    "results_count": 1,
    "results": [{
      "asin": "B0DYTF8L2W",
      "title": "Apple AirPods Pro 3",
      "price": "$249.00",
      "rating": 4.7,
      "ratings_total": 12583,
      "availability": "In Stock",
      "seller": "Apple",
      "brand": "Apple"
    }]
  }
```

### 3. 关键词搜索（支持全球 13 站点）

```bash
user@openclaw:~$ python3 scripts/pangolin.py --q "wireless mouse" --site amz_jp

  > [Pangolin API] Searching amz_jp for "wireless mouse"...
  > [Parser: amzKeyword] Parsing search results...

  {
    "success": true,
    "results_count": 16,
    "results": [
      {"asin": "B09BV1DKKP", "title": "ロジクール ワイヤレスマウス M750", "price": "¥4,950", "rating": 4.5},
      {"asin": "B0D1XGR1BH", "title": "Razer Viper V3 HyperSpeed", "price": "¥18,980", "rating": 4.8},
      {"asin": "B08L5TNJHQ", "title": "エレコム ワイヤレスマウス M-SH30DBSK", "price": "¥2,373", "rating": 4.3},
      ...
    ]
  }
```

### 4. 评论分析（星级过滤 + 多页抓取）

```bash
user@openclaw:~$ python3 scripts/pangolin.py --asin B076CLQDR4 --mode review \
                    --filter-star critical --pages 2 --site amz_us

  > [Pangolin API] Fetching reviews for B076CLQDR4 (pages: 1-2)...
  > [Parser: amzReviewV2] Filtering by: critical stars...

  {
    "success": true,
    "results_count": 20,
    "results": [
      {"rating": 1, "title": "Stopped working after 2 weeks", "date": "2025-03-10",
       "text": "The battery dies within 3 hours. Terrible build quality..."},
      {"rating": 2, "title": "Not worth the price", "date": "2025-03-08",
       "text": "Connection drops every 10 minutes. Returning this..."},
      ...
    ]
  }
```

---

> 查询 1 积分/次 | 评论 5 积分/页 | Follow Seller 1 积分/次 | 支持 13 个亚马逊站点 | 详见 SKILL.md 获取完整 CLI 参数列表
