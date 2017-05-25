---
title: "オプション (SQL Server オブジェクト エクスプローラー - [スクリプト作成] ページ) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.ObjectExplorerScripting
- VS.ToolsOptionsPages.Sql_Server_Object_Explorer.ObjectExplorerScripting
ms.assetid: 6105aec9-1b72-4cb2-bd24-fc35f6d95240
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d5353c0732833516e95cc734a2d7bbe0f1258554
ms.lasthandoff: 04/11/2017

---
# <a name="options-sql-server-object-explorer---scripting-page"></a>オプション (SQL Server オブジェクト エクスプローラー - [スクリプト作成] ページ)
このページを使用すると、**オブジェクト エクスプローラー**内にあるオブジェクトのコンテキスト メニューの次の各コマンドに適用されるスクリプト オプションを設定できます。  
  
-   ユーザー テーブルおよびビューに対する **[編集]** コマンド。  
  
-   ユーザーが作成したオブジェクトに対する **[<object> をスクリプト化]** コマンド。  
  
-   ユーザーが作成したオブジェクトに対する **[変更]** コマンド。  
  
-   このページでは、 **SQL Server スクリプト生成ウィザード**で使用するスクリプト オプションの既定値も設定できます。  
  
## <a name="remarks"></a>解説  
**[編集]** コマンドおよび **[変更]** コマンドを実行した場合は、同じオプション設定に対して **[<object> をスクリプト化]** コマンドを実行した場合と異なる結果になることがあります。 **[編集]** コマンドおよび **[変更]** コマンドは、クエリ エディター セッション中に現在のデータベースでオブジェクトを変更するために設計されています。 **[<object> をスクリプト化]** コマンドは、後でオブジェクトの作成に使用できるスクリプトを生成するために設計されています。  
  
## <a name="options"></a>オプション  
スクリプト オプションを指定するには、各オプションの右にあるリストから、いずれかの設定を選択します。  
  
### <a name="general-scripting-options"></a>[全般スクリプト作成オプション]  
**[各ステートメントを区切る]**  
バッチ区切り記号を使用して、個々の [!INCLUDE[tsql](../../includes/tsql_md.md)] ステートメントを区切ります。 **クエリ エディター**の既定のバッチ区切り記号を変更するには、 **[ツール]**/**[オプション]**/**[クエリ実行]**/**[SQL Server]**/**[全般]**/**[バッチ区切り記号]**の順に選択します。 既定値は False です。 詳細については、「 [GO (Transact-SQL)](http://msdn.microsoft.com/en-us/b2ca6791-3a07-4209-ba8e-2248a92dd738)」を参照してください。  
  
**[説明用ヘッダーを含める]**  
スクリプトをオブジェクトごとのセクションに分割し、説明用のコメントを追加します。 既定値は True です。 詳細については、「 [/*...*/ (コメント) (Transact-SQL)](http://msdn.microsoft.com/en-us/4d9ab1b2-4bbb-4c16-beb1-cafc1af7417c)」を参照してください。  
  
**[VarDecimal オプションを含める]**  
vardecimal ストレージ オプションを含めます。 既定値は False です。 詳細については、「 [sp_db_vardecimal_storage_format (Transact-SQL)](http://msdn.microsoft.com/en-us/9920b2f7-b802-4003-913c-978c17ae4542)」を参照してください。  
  
**[変更の追跡のスクリプトを作成]**  
変更の追跡の情報をスクリプトに含めます。  
  
**[サーバーのバージョン互換のスクリプト]**  
選択したバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]で実行できるスクリプトを作成します。 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] の新機能のスクリプトを以前のバージョン用に生成することはできません。 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] 用に作成したスクリプトには、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]で動作しているサーバーや、以前の [データベース互換性レベルの設定](http://msdn.microsoft.com/en-us/ca5fd220-d5ea-4182-8950-55d4101a86f6)が適用されているデータベースに対して実行できないものもあります。  
  
**[フルテキスト カタログのスクリプトを作成]**  
フルテキスト カタログのスクリプトを含めます。 既定値は False です。 詳細については、「 [CREATE FULLTEXT CATALOG (Transact-SQL)](http://msdn.microsoft.com/en-us/d7a8bd93-e2d7-4a40-82ef-39069e65523b)」を参照してください。  
  
**[USE のスクリプトを作成] <database>**  
スクリプトに USE &lt;データベース&gt; ステートメントを追加することにより、現在の **オブジェクト エクスプローラー** データベースのコンテキストでデータベース オブジェクトを作成します。 スクリプトが別のデータベースで使用される可能性がある場合は、False を選択して除外します。 既定値は True です。 詳細については、「 [USE (Transact-SQL)](http://msdn.microsoft.com/en-us/c05acac8-c063-4770-8e36-d7f71d500b10)」を参照してください。  
  
### <a name="object-scripting-options"></a>[オブジェクト スクリプト作成オプション]  
**[依存オブジェクトのスクリプトを生成する]**  
選択したオブジェクトのスクリプトを実行する際に必要な追加オブジェクトのスクリプトを生成します。 既定値は False です。  
  
**[IF NOT EXISTS 句を含める]**  
各オブジェクトを作成する前にデータベースにそのオブジェクトが存在しないことを確認するためのステートメントを含めます。 既定値は False です。 詳細については、「 [IF...ELSE (Transact-SQL)](http://msdn.microsoft.com/en-us/676c881f-dee1-417a-bc51-55da62398e81) 」と「 [EXISTS (Transact-SQL)](http://msdn.microsoft.com/en-us/b6510a65-ac38-4296-a3d5-640db0c27631)」を参照してください。  
  
**[オブジェクト名を修飾するスキーマ]**  
オブジェクト名をオブジェクト スキーマで修飾します。 既定値は False です。 詳細については、「 [データベース スキーマの作成](http://msdn.microsoft.com/en-us/ed2a5522-f4d2-4111-95a4-d3e1e5081739)」を参照してください。  
  
**[拡張プロパティのスクリプトを作成]**  
オブジェクトに拡張プロパティが含まれている場合、それらの拡張プロパティをスクリプトに追加します。 既定値は False です。 詳細については、「 [sp_addextendedproperty (Transact-SQL)](http://msdn.microsoft.com/en-us/565483ea-875b-4133-b327-d0006d2d7b4c)」を参照してください。  
  
**[所有者のスクリプトを作成]**  
生成されたスクリプトに所有者を含めます。 既定値は False です。  
  
**[権限のスクリプトを作成]**  
データベース オブジェクトに対する権限をスクリプトに含めます。 既定値は True です。 詳細については、「 [アクセス許可](http://msdn.microsoft.com/en-us/f28e3dea-24e6-4a81-877b-02ec4c7e36b9)」を参照してください。  
  
### <a name="tableview-options"></a>[テーブル/ビュー オプション]  
次のオプションは、テーブルまたはビューのスクリプトのみに適用されます。  
  
**[ユーザー定義データ型から基本データ型に変換します]**  
ユーザー定義データ型を元の基本型に変換します。 スクリプトを実行するデータベースに、ソース データベースのユーザー定義データ型が存在しない場合は、True を使用します。 ユーザー定義データ型を保持する場合は、False を使用します。 既定値は False です。 詳細については、「 [CREATE TYPE (Transact-SQL)](http://msdn.microsoft.com/en-us/2202236b-e09f-40a1-bbc7-b8cff7488905)」を参照してください。  
  
**[SET ANSI PADDING コマンドを生成する]**  
各 CREATE TABLE ステートメントの前後に SET ANSI_PADDING ステートメントを追加します。 既定値は True です。 詳細については、「 [SET ANSI_PADDING (Transact-SQL)](http://msdn.microsoft.com/en-us/92bd29a3-9beb-410e-b7e0-7bc1dc1ae6d0)」を参照してください。  
  
**[照合順序を含める]**  
列定義に照合順序を含めます。 既定値は True です。 詳細については、「 [Collation and Unicode Support](http://msdn.microsoft.com/en-us/92d34f48-fa2b-47c5-89d3-a4c39b0f39eb)」を参照してください。  
  
**[IDENTITY プロパティを含める]**  
IDENTITY シードおよび IDENTITY インクリメントの定義を含めます。 既定値は True です。 詳細については、「 [IDENTITY (プロパティ) (Transact-SQL)](http://msdn.microsoft.com/en-us/8429134f-c821-4033-a07c-f782a48d501c)」を参照してください。  
  
**[外部キー参照を修飾するスキーマ]**  
FOREIGN KEY 制約のテーブル参照にスキーマ名を追加します。 既定値は True です。  
  
**[バインドされた既定値およびルールのスクリプトを作成]**  
バインド ストアド プロシージャ **sp_bindefault** および **sp_bindrule** の呼び出しを含めます。 既定値は True です。 詳細については、「 [sp_bindefault (Transact-SQL)](http://msdn.microsoft.com/en-us/3da70c10-68d0-4c16-94a5-9e84c4a520f6) 」と「 [sp_bindrule (Transact-SQL)](http://msdn.microsoft.com/en-us/2606073e-c52f-498d-a923-5026b9d97e67)」を参照してください。  
  
**[CHECK 制約のスクリプトを作成]**  
スクリプトに [CHECK 制約](http://msdn.microsoft.com/en-us/637098af-2567-48f8-90f4-b41df059833e) を追加します。 既定値は True です。  
  
**[既定のスクリプトを作成]**  
スクリプトに列の既定値を含めます。 既定値は False です。 詳細については、「 [CREATE DEFAULT (Transact-SQL)](http://msdn.microsoft.com/en-us/08475db4-7d90-486a-814c-01a99d783d41)」を参照してください。  
  
**[ファイル グループのスクリプトを作成]**  
テーブル定義で ON 句にファイル グループを指定します。 既定値は False です。 詳細については、「 [CREATE TABLE (Transact-SQL)](http://msdn.microsoft.com/en-us/1e068443-b9ea-486a-804f-ce7b6e048e8b)」を参照してください。  
  
**[外部キーのスクリプトを作成]**  
スクリプトに [FOREIGN KEY 制約](http://msdn.microsoft.com/en-us/31fbcc9f-2dc5-4bf9-aa50-ed70ec7b5bcd) を含めます。 既定値は False です。  
  
**[フルテキスト インデックスのスクリプトを作成]**  
スクリプトにフルテキスト インデックスを含めます。 既定値は False です。 詳細については、「 [CREATE FULLTEXT INDEX (Transact-SQL)](http://msdn.microsoft.com/en-us/8b80390f-5f8b-4e66-9bcc-cabd653c19fd)」を参照してください。  
  
**[インデックスのスクリプトを作成]**  
スクリプトにクラスター化、非クラスター化、および XML インデックスを含めます。 既定値は True です。 詳細については、「 [CREATE INDEX (Transact-SQL)](http://msdn.microsoft.com/en-us/d2297805-412b-47b5-aeeb-53388349a5b9)」を参照してください。  
  
**[パーティション構成のスクリプトを作成]**  
スクリプトにテーブル パーティション分割構成を含めます。 既定値は False です。 詳細については、「 [CREATE PARTITION SCHEME (Transact-SQL)](http://msdn.microsoft.com/en-us/5b21c53a-b4f4-4988-89a2-801f512126e4)」を参照してください。  
  
**[主キーのスクリプトを作成]**  
スクリプトに [PRIMARY KEY 制約](http://msdn.microsoft.com/en-us/31fbcc9f-2dc5-4bf9-aa50-ed70ec7b5bcd) を含めます。 既定値は True です。  
  
**[統計のスクリプトを作成]**  
スクリプトにユーザー定義統計を含めます。 既定値は False です。 詳細については、「 [CREATE STATISTICS (Transact-SQL)](http://msdn.microsoft.com/en-us/b23e2f6b-076c-4e6d-9281-764bdb616ad2)」をご覧ください。  
  
**[トリガーのスクリプトを作成]**  
スクリプトにトリガーを含めます。 既定値は False です。 詳細については、「 [CREATE TRIGGER (Transact-SQL)](http://msdn.microsoft.com/en-us/edeced03-decd-44c3-8c74-2c02f801d3e7)」をご覧ください。  
  
**[一意キーのスクリプトを作成]**  
スクリプトに [UNIQUE 制約と CHECK 制約](http://msdn.microsoft.com/en-us/637098af-2567-48f8-90f4-b41df059833e) を含めます。 既定値は False です。  
  
**[ビュー列のスクリプトを作成]**  
ビュー ヘッダーにビュー列を宣言します。 既定値は False です。 詳細については、「 [CREATE VIEW (Transact-SQL)](http://msdn.microsoft.com/en-us/aecc2f73-2ab5-4db9-b1e6-2f9e3c601fb9)」を参照してください。  
  
**[[ScriptDriIncludeSystemNames]]**  
宣言参照整合性を適用するために、システムによって生成される制約名を含めます。 既定値は False です。 詳細については、「 [REFERENTIAL_CONSTRAINTS (Transact-SQL)](http://msdn.microsoft.com/en-us/5d358f18-0a85-4b55-af4b-98d5f4cd1020)」を参照してください。  
  
## <a name="see-also"></a>参照  
[スクリプトの生成 (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/9711c617-3c68-4e5a-aea3-befc64d51524)  
  
