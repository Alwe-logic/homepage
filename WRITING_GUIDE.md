# ノート執筆ガイド

定義・定理などを使うノートは、拡張子を `.mdx` にします。frontmatter の直後でコンポーネントを読み込みます。

```mdx
import MathStatement from '../../components/MathStatement.astro';
```

日本語ノートからの基本的な書き方は次の通りです。

```mdx
<MathStatement kind="definition" number="1" title="順序数">

ここに定義を書きます。数式も $\alpha<\beta$ のように書けます。

</MathStatement>

<MathStatement kind="theorem" number="2" title="主定理">

ここに定理を書きます。

</MathStatement>

<MathStatement kind="proof">

ここに証明を書きます。

</MathStatement>
```

`kind` には次の値を指定できます。番号と題名は省略可能です。

| kind | 日本語 | English |
| --- | --- | --- |
| `definition` | 定義 | Definition |
| `theorem` | 定理 | Theorem |
| `proposition` | 命題 | Proposition |
| `lemma` | 補題 | Lemma |
| `corollary` | 系 | Corollary |
| `remark` | 注意 | Remark |
| `example` | 例 | Example |
| `conjecture` | 予想 | Conjecture |
| `problem` | 問題 | Problem |
| `exercise` | 演習問題 | Exercise |
| `claim` | 主張 | Claim |
| `proof` | 証明 | Proof |

LaTeX原稿と同じように節ごとの共通番号にしたい場合は、`number="2.3"` のように番号を指定します。定義・定理・命題などで同じ番号列を手動で共有できます。

英語版の深い階層にあるノートでは、読み込み部分を次のようにします。

```mdx
import MathStatement from '../../../components/MathStatement.astro';
```

## 文献を引用する

本文中の引用番号と参考文献を対応させる場合は、`Citation` と `Reference` も読み込みます。

```mdx
import Citation from '../../components/Citation.astro';
import Reference from '../../components/Reference.astro';
```

本文では、引用した主張の直後に次のように書きます。`source` は、その文献だけに使う短い識別名です。

```mdx
この同値性は先行研究で示されています<Citation number="1" source="sample2026" />。
```

定理番号や頁まで示したい場合は `locator` を追加できます。

```mdx
<Citation number="1" source="sample2026" locator="Thm. 3.2" />
```

ノート末尾の参考文献一覧では、`Reference` の `id` を本文中の `source` と一致させます。DOIがある場合はDOIを、プレプリントだけの場合はarXivのabsページをリンク先にします。

```mdx
## 参考文献

<ol className="reference-list">
  <Reference
    id="sample2026"
    number={1}
    href="https://doi.org/10.xxxx/example"
  >
    A. Author, “Paper title,” *Journal* **12** (3), 45–67, 2026.
  </Reference>
</ol>
```

査読前のプレプリント、学位論文、講演資料は、その種類と公開・未公刊の別を明記します。外部文献から得た事実と、自分の計算・予想・未証明の主結果も本文中で区別してください。
