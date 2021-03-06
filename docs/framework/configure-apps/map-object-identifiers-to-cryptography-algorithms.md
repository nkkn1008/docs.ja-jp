---
title: "暗号化アルゴリズムへのオブジェクト ID の割り当て"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: dbfe394193925e38dad774d39d79ac813abef22a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>暗号化アルゴリズムへのオブジェクト ID の割り当て
デジタル署名は、データが改ざんされない 1 つのプログラムから別の送信時を確認します。 通常、デジタル署名は、数学関数に署名するデータのハッシュを適用して計算されます。 署名するハッシュ値を書式設定時に一部のデジタル署名アルゴリズムは、書式設定操作の一部として ASN.1 オブジェクト識別子 (OID) を追加します。 OID は、ハッシュの計算に使用されたアルゴリズムを識別します。 アルゴリズムは、カスタム アルゴリズムを使用する暗号化機構を拡張するオブジェクトの識別子にマップできます。 次の例では、オブジェクト識別子を新しいハッシュ アルゴリズムにマップする方法を示します。  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 [ \<OidEntry > 要素](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)2 つの属性が含まれています。 **OID**属性は、オブジェクトの識別番号。 **名前**属性の値が、**名前**属性から、 [ \<nameEntry > 要素](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)です。 オブジェクト識別子は、簡易名にマップできる前に、クラスにアルゴリズム名をマッピングする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [暗号化クラスの設定](../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)
