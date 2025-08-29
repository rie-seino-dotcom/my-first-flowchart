graph TD
    subgraph customer
        direction LR
        A[顧客<br>(作業者)]
    end

    subgraph tool
        direction LR
        B[Gmail]
        C[Salesforce]
    end
    
    subgraph support
        direction LR
        D[サポート<br>(作業者)]
    end

    subgraph committee
        direction LR
        J[合理的配慮委員会<br>(作業者)]
    end
    
    subgraph hiring
        direction LR
        K[採用<br>(作業者)]
    end

    A -- メール送付 --> B
    B -- 転送 --> C
    C -- ケース作成 --> D
    
    D -- 一次仕分け: 営業メールなど --> E[返信対象外のフラグをつける]
    D -- 一次仕分け: 採用関連 --> F[採用関連のフラグをつける]
    F -- Slackで連携 --> K
    D -- 一次仕分け: 合理的配慮窓口としての回答が必要 --> J
    
    J -- 回答が必要 --> G[窓口回答必須フラグをつける]
    J -- 回答が不要 --> I[返信対象外フラグをつける]
    
    G -- 返信 --> H[サポートが返信を行う]
    I -- 返信 --> H
    
    H -- 完了 --> M[終了]
    K -- 返信を行う --> L[採用が返信を行う]
    L -- 完了 --> M
    E -- 完了 --> M
