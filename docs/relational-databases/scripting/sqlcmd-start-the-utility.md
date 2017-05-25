---
title: "sqlcmd ユーティリティの起動 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
caps.latest.revision: 41
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9f213219f9d9fd65af0fee8544f64e61fc1151a3
ms.lasthandoff: 04/11/2017

---
# <a name="sqlcmd---start-the-utility"></a>sqlcmd - ユーティリティの起動
  [sqlcmd ユーティリティ](../../tools/sqlcmd-utility.md) を使用すると、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント、システム プロシージャ、およびスクリプト ファイルを、コマンド プロンプト、SQLCMD モードのクエリ エディター、Windows スクリプト ファイル、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブのオペレーティング システム (Cmd.exe) ジョブ ステップで入力できます。
> [!NOTE]  
>  **sqlcmd**の既定の認証は Windows 認証です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用するには、 **-U** オプションと **-P** オプションを追加して、ユーザー名とパスワードを指定する必要があります。  
  
> [!NOTE]  
>  既定では、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] は名前付きインスタンスの **sqlexpress**としてインストールされます。  
  
### <a name="start-the-sqlcmd-utility-and-connect-to-a-default-instance-of-sql-server"></a>sqlcmd ユーティリティを起動し、SQL Server の既定のインスタンスに接続する  
  
1.  **[スタート]** ボタンをクリックし、 **[ファイル名を指定して実行]**をクリックします。 **[名前]** ボックスに「 **cmd**」と入力して、 **[OK]** をクリックします。コマンド プロンプト ウィンドウが開きます ( [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のこのインスタンスに接続したことがない場合、接続を受け入れるには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の構成が必要になることがあります)。  
  
2.  コマンド プロンプトで、「 **sqlcmd**」と入力します。  
  
3.  Enter キーを押します。  
  
     これで、コンピューターで実行している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスに、信頼できる接続を確立しました。  
  
     **1>** は **sqlcmd** プロンプトであり、行番号を表しています。 Enter キーを押すたびに、この番号が 1 ずつ増えます。  
  
4.  **sqlcmd** セッションを終了するには、 **sqlcmd** プロンプトで「 **EXIT** 」と入力します。  
  
### <a name="start-the-sqlcmd-utility-and-connect-to-a-named-instance-of-sql-server"></a>sqlcmd ユーティリティを起動し、SQL サーバーの名前付きインスタンスに接続する  
  
1.  コマンド プロンプト ウィンドウを開き、「 **sqlcmd -S***myServer\instanceName*」と入力します。 *myServer\instanceName* には、コンピューターの実際の名前と、接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを指定してください。  
  
2.  Enter キーを押します。  
  
     **sqlcmd** プロンプト (1>) は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の指定されたインスタンスに接続していることを示します。  
  
    > [!NOTE]  
    >  入力した [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントはバッファーに格納されます。 GO コマンドが見つかると、ステートメントがバッチとして実行されます。  
  
## <a name="see-also"></a>参照  
 [sqlcmd を使用した Transact-SQL スクリプト ファイルの実行](../../relational-databases/scripting/sqlcmd-run-transact-sql-script-files.md)  
  
  