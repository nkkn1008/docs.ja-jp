---
title: "Windows Communication Foundation バインディング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d6fd1bf29af743e5bfcd466ffdf7430c389635de
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="windows-communcation-foundation-bindings"></a>Windows Communication Foundation バインディング
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、アプリケーション ソフトウェアを作成する方法と、アプリケーション ソフトウェアが他のソフトウェアと通信する方法は分離されています。 バインディングを使用して、クライアントとサービスが相互に通信するために必要なトランスポート、エンコーディング、およびプロトコルの詳細を指定します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、バインディングを使用してエンドポイントの基になるネットワーク上の表現を生成します。このため、バインディングの詳細の大半について通信している双方が合意する必要があります。 これを実現する最も簡単な方法は、サービスのクライアントがサービスのエンドポイントと同じバインディングを使用することです。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]を参照してください方法[Windows Communication Foundation サービスを構成してクライアントを使用してバインド](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)です。  
  
 バインディングは、バインド要素のコレクションで構成されます。 各要素は、エンドポイントがクライアントと通信する方法の一部分を記述します。 バインディングには、1 つ以上のトランスポート バインド要素、1 つ以上のメッセージ エンコーディング バインド要素 (既定では、トランスポート バインド要素によって提供されます)、および任意の数の他のプロトコル バインド要素が含まれている必要があります。 このように、ランタイムをビルドするプロセスでは、各バインド要素からランタイムにコードを提供できます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、一般的なバインド要素を含むさまざまなバインディングが用意されています。 これらのバインディングは、既定の設定で使用することも、ユーザーの要件に応じて既定値を変更することもできます。 これらのシステム指定のバインディングには、バインド要素およびその設定を直接制御できるプロパティが含まれます。 また、バインディングの各バージョンに独自の名前を付けることで、複数のバージョンを同時に使用することもできます。 詳細については、「 [Configuring System-Provided バインド](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)です。  
  
 システム指定のバインディングに用意されていないバインド要素のコレクションが必要になった場合には、その必要なバインド要素のコレクションで構成されるカスタム バインディングを作成できます。 このようなカスタム バインディングは簡単に作成でき、新しいクラスも必要ありませんが、バインド要素およびその設定を制御するためのプロパティは提供されません。 バインド要素へのアクセスと設定の変更は、バインド要素を含むコレクションを通じて行います。 詳細については、「[カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [システム指定のバインディングを構成します。](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 一般的なシナリオをサポートするために [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に用意されたバインディングを使用および変更する方法について説明します。  
  
 [バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 サービスおよびクライアントで使用する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] バインディングをコードで強制的に定義する方法と、構成を使用して宣言によって定義する方法について説明します。  
  
 [カスタム バインド](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 <xref:System.ServiceModel.Channels.CustomBinding> の概要と使用する状況について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>関連項目  
 [バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)
