# my-first-flowchartgraph TD
    subgraph 顧客 (作業者)
        A[合理的配慮窓口にメールを送付]
    end

    subgraph ツール
        B[Gmail]
        C[Salesforce]
    end
    
    subgraph サポート (作業者)
        D{一次仕分け}
        E[返信対象外のフラグをつける]
        F[採用関連のフラグをつける]
        G[窓口回答必須フラグをつける]
        H[返信を行う]
        I[返信対象外フラグをつける]
    end

    subgraph 合理的配慮委員会 (作業者)
        J{回答が必要か判断}
    end
    
    subgraph 採用 (作業者)
        K[Slackで連携]
        L[返信を行う]
    end

    A -- メール送付 --> B
    B -- 転送 --> C
    C -- ケース作成 --> D
    
    D -- 営業メールなど --> E
    D -- 採用関連 --> F
    F -- Slackで連携 --> K
    D -- 合理的配慮窓口としての回答が必要 --> J
    
    J -- 回答が必要 --> G
    J -- 回答が不要 --> I
    
    G -- 返信 --> H
    I -- 返信 --> H
    
    H -- 完了 --> M[終了]
    L -- 完了 --> M
    E -- 完了 --> M
    K -- 完了 --> L
