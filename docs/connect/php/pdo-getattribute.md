---
title: :Getattribute |Microsoft ドキュメント
ms.custom: ''
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c81833ea-8b8a-459d-8f24-920098da994d
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 56e0fc4e6cf98af6b688fe3752b7b57eda134341
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="pdogetattribute"></a>PDO::getAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

定義済み PDO またはドライバーの属性の値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
mixed PDO::getAttribute ( $attribute )  
```  
  
#### <a name="parameters"></a>パラメーター  
*$attribute*: サポートされる属性のいずれか。 サポートされる属性の一覧については、「解説」セクションを参照してください。  
  
## <a name="return-value"></a>戻り値  
成功した場合、接続オプション、定義済み PDO 属性、またはカスタム ドライバー属性の値を返します。 エラーが発生した場合は null を返します。  
  
## <a name="remarks"></a>解説  
次の表に、サポートされる属性の一覧を示します。  
  
|属性|処理を行った機能|サポートされる値|Description|  
|-------------|----------------|--------------------|---------------|  
|PDO::ATTR_CASE|PDO|PDO::CASE_LOWER<br /><br />PDO::CASE_NATURAL<br /><br />PDO::CASE_UPPER|列名に必要な大文字/小文字の使い分けを指定します。 PDO::CASE_LOWER は、列名を強制的に小文字にします。PDO::CASE_NATURAL は、列名をデータベースによって返されたままの状態にします。PDO::CASE_UPPER は、列名を強制的に大文字にします。<br /><br />既定値は、PDO::CASE_NATURAL です。<br /><br />この属性は、PDO::setAttribute を使用して設定することもできます。|  
|PDO::ATTR_CLIENT_VERSION|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|string の配列|ドライバーおよび関連するライブラリのバージョンを記述します。 次の要素の配列を返します: ODBC のバージョン (*MajorVer*.*MinorVer*)、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ネイティブ クライアント DLL の名前とバージョン、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]バージョン (*MajorVer*.*MinorVer*.*BuildNumber*.*リビジョン*)|  
|PDO::ATTR_DRIVER_NAME|PDO|文字列|常に "sqlsrv" を返します。|  
|PDO::ATTR_DRIVER_VERSION|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|文字列|示します、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]バージョン (*MajorVer*.*MinorVer*.*BuildNumber*.*リビジョン*)|  
|PDO::ATTR_ERRMODE|PDO|PDO::ERRMODE_SILENT<br /><br />PDO::ERRMODE_WARNING<br /><br />PDO::ERRMODE_EXCEPTION|ドライバーがエラーを処理する方法を指定します。<br /><br />PDO::ERRMODE_SILENT (既定値) は、エラー コードと情報を設定します。<br /><br />PDO::ERRMODE_WARNING は、E_WARNING を生成します。<br /><br />PDO::ERRMODE_EXCEPTION は、例外を生成します。<br /><br />この属性は、PDO::setAttribute を使用して設定することもできます。|  
|PDO::ATTR_ORACLE_NULLS|PDO|PDO のドキュメントを参照してください。|PDO のドキュメントを参照してください。|  
|PDO::ATTR_SERVER_INFO|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|3 つの要素の配列|現在のデータベース、SQL Server のバージョン、および SQL Server のインスタンスを返します。|  
|PDO::ATTR_SERVER_VERSION|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|文字列|SQL Server のバージョンを示します (*メジャー*.*マイナー*.*BuildNumber*)|  
|PDO::ATTR_STRINGIFY_FETCHES|PDO|PDO のドキュメントを参照してください。|PDO のドキュメントを参照してください。|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|PHP メモリの制限に 1。|クライアント側カーソルの結果セットを保持するバッファーのサイズを設定します。<br /><br />既定では 10,240 KB (10 MB) です。<br /><br />クライアント側のカーソルの詳細については、次を参照してください。[カーソルの種類&#40;SQLSRV ドライバー&#41;](../../connect/php/cursor-types-sqlsrv-driver.md)です。|  
|PDO::SQLSRV_ATTR_DIRECT_QUERY|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true<br /><br />オプション|クエリの直接実行または準備された実行を指定します。 詳細については、「 [Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)」 (PDO_SQLSRV ドライバーでの直接ステートメント実行と準備されたステートメントの実行) を参照してください。|  
|PDO::SQLSRV_ATTR_ENCODING|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|PDO::SQLSRV_ENCODING_UTF8<br /><br />PDO::SQLSRV_ENCODING_SYSTEM|ドライバーがサーバーとの通信に使用する文字セット エンコーディングを指定します。<br /><br />既定値は PDO::SQLSRV_ENCODING_UTF8 です。|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true または false|数値の SQL 型 (ビット、integer、smallint、tinyint、float または real) と列からの数値のフェッチを処理します。<br /><br />オンの接続オプション フラグ ATTR_STRINGIFY_FETCHES SQLSRV_ATTR_FETCHES_NUMERIC_TYPE が有効になっている場合でも、戻り値は文字列です。<br /><br />バインド列で返される PDO 型 PDO_PARAM_INT がある場合は、SQLSRV_ATTR_FETCHES_NUMERIC_TYPE がオフの場合でも、int は整数型の列からの戻り値です。|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|整数 (integer)|クエリのタイムアウト (秒単位) を設定します。<br /><br />既定値は 0 であり、ドライバーは結果をいつまでも待ちます。<br /><br />負の数値は許可できません。|  

  
一部の定義済み属性は PDO で処理されますが、他の属性はドライバーで処理する必要があります。 ドライバーでは、すべてのカスタム属性および接続オプションが処理され、サポートされていない属性または接続オプションは null を返します。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
次の例では、値を変更する前と後の PDO::ATTR_ERRMODE 属性の値を示します。  
  
```  
<?php  
$database = "AdventureWorks";  
$conn = new PDO( "sqlsrv:server=(local) ; Database = $database", "", "");  
  
$attributes1 = array( "ERRMODE" );  
foreach ( $attributes1 as $val ) {  
     echo "PDO::ATTR_$val: ";  
     var_dump ($conn->getAttribute( constant( "PDO::ATTR_$val" ) ));  
}  
  
$conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  
  
$attributes1 = array( "ERRMODE" );  
foreach ( $attributes1 as $val ) {  
     echo "PDO::ATTR_$val: ";  
     var_dump ($conn->getAttribute( constant( "PDO::ATTR_$val" ) ));  
}  
  
// An example using PDO::ATTR_CLIENT_VERSION  
print_r($conn->getAttribute( PDO::ATTR_CLIENT_VERSION ));  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDO クラス](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
