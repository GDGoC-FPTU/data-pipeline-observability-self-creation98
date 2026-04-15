# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** 2A202600268
**Name:** Phạm Thanh Tùng
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | Agent: Based on my data, the best choice is Laptop at $1200. | 9 | Dung san pham, dung gia, ket qua chinh xac |
| Garbage Data (`garbage_data.csv`) | Agent: Based on my data, the best choice is Nuclear Reactor at $999999. | 1 | Sai hoan toan, chon outlier vo nghia |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Khi su dung du lieu rac (garbage data), Agent da tra loi hoan toan sai vi nhieu ly do lien quan den chat luong du lieu dau vao. Thu nhat, du lieu chua Duplicate IDs (id=1 xuat hien hai lan voi san pham khac nhau), khien Agent khong the phan biet chinh xac giua cac san pham. Thu hai, cot price co gia tri sai kieu du lieu (vi du: "ten dollars" thay vi so), lam cho viec tinh toan va so sanh gia tro nen khong dang tin cay. Thu ba, du lieu chua extreme outlier nhu Nuclear Reactor voi gia 999999 dollar, day la gia tri bat thuong khien Agent chon no la san pham tot nhat chi vi gia cao nhat, mac du no khong phai la san pham electronics hop ly. Thu tu, cac truong null values (id=None, category=None) tao ra cac record khong co y nghia, lam nhiem du lieu. Tat ca nhung van de nay cho thay rang neu khong co buoc Data Validation va Data Cleaning truoc khi dua du lieu vao AI Agent, ket qua tra ve se hoan toan sai lech va khong the tin tuong duoc. Pipeline ETL voi buoc validation giup loai bo cac record loi, dam bao Agent chi lam viec voi du lieu sach va cho ket qua chinh xac.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y hoan toan. Du prompt co tot den dau, neu du lieu dau vao bi loi (outliers, duplicates, null values, wrong types) thi Agent van se cho ra ket qua sai. Data Quality la nen tang quan trong nhat cua bat ky he thong AI nao. Mot pipeline ETL tot voi validation chat che se dam bao du lieu sach, tu do giup Agent dua ra cau tra loi chinh xac va dang tin cay hon.
