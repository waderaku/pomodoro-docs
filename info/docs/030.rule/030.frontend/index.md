#　フロントエンドルール

- 再利用性を下げない範囲において、propsの使用は控え、カスタムフックからrecoilのデータを受け取る。
    - ex:taskIdはPropsで渡し、taskの中身についてはRecoilから受け取る
- コンポーネントから直接Recoil操作をしない
    - 必ず、カスタムhookを挟む
    - Recoilは状態を管理、カスタムフックは状態の振る舞いを管理、コンポーネントは画面の見え方を管理する
    - 参考:[Recoilで始めるお手軽フロントエンドDDD](https://zenn.dev/susiyaki/articles/95dea88e673e1f854130#recoil-%E3%81%A7%E8%A1%8C%E3%81%86%E3%83%89%E3%83%A1%E3%82%A4%E3%83%B3%E9%A7%86%E5%8B%95%E8%A8%AD%E8%A8%88%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8)



