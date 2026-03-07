# RVSS 人事DB スプレッドシート構築

## 作成済みスプレッドシート

| ファイル名 | スプレッドシートID | 概要 |
|---|---|---|
| RVSS_メンバー名簿 | `1sRrLVbJSByzPT9R047HZwqfEGfnhhn9GdK7Wo4faYOo` | メンバーマスター。流入経路から自動反映、ステータスはドロップダウン |
| RVSS_流入経路・採用管理 | `1j1fSuqy7xCEtx5h6i2_C9KO1lx_iL7BNO3bHu6A62zI` | 採用管理。90名分の静的データ。メンバー名簿の参照元 |
| RVSS_出席管理 | `13F_0lX9bdndKzRXwgdYyWFQNhYG5828FM8EWsgieGgE` | meeting / meeting_member / session / member |
| RVSS_出欠_E008 | `1FQg-Bd-RHOMgUVJXUeppC1tA-_zbTdl5unHThjq0MNU` | 人事定例。フォーム連携済み、出席/遅刻/欠席自動判定、日別出欠シートあり |

## データフロー

```
流入経路・採用管理（静的）
    ↓ IMPORTRANGE
メンバー名簿（マスター）

RVSS_出席管理
├── meeting（E001〜E014）
├── meeting_member（181件）
├── session（週次自動生成）
└── member（RVSS個人管理シートから参照）

RVSS_出欠_[MTG_id]（MTGごとに個別作成・ホストに権限付与）
├── フォーム回答（Googleフォーム連携）
├── log（出席/遅刻/欠席自動判定）
└── 日別出欠（出席者/欠席者/遅刻者/名前不一致）
```

## 今後の予定

- [ ] RVSS_出欠_E001〜E007, E009〜E014（各MTGの出欠管理）
- [ ] オンボーディング管理
- [ ] 360度評価
