---
title: "Utilização do associador de serialização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e35df7934ffb330feb45e5ff7167c9715f2d291e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="usage-of-serialization-binder"></a>Utilização do associador de serialização
Este exemplo mostra como usar o <xref:System.Runtime.Serialization.SerializationBinder> para alterar a versão de um tipo genérico quando ele é serializado.  
  
## <a name="demonstrates"></a>Demonstra  
 <xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>Discussão  
 Este exemplo mostra como duas entidades que são destinados a versões diferentes do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] podem se comunicar usando o formatador binário e o associador de serialização.  
  
 O desenvolvimento deste exemplo foi realizado usando a comunicação remota do .NET. O exemplo consiste em um servidor de destino [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], que implementa um contrato com tipos genéricos e dois clientes diferentes, um direcionamento [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] e o direcionamento de outro [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].  
  
 As conexões de servidor um <xref:System.Runtime.Serialization.SerializationBinder> para o formatador binário para poder alterar a versão dos tipos adequadamente na serialização, então ambos os clientes podem desserializar esses tipos corretamente.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar e executar o exemplo  
  
1.  Para executar o cliente, clique com botão direito a solução, SBGenericsVTS (6 projetos) e, em seguida, selecione **propriedades**.  
  
2.  Em **propriedades comuns**, selecione **projeto de inicialização**, em seguida, selecione **vários projetos de inicialização**.  
  
3.  Selecione **servidor** primeiro, em seguida, **Client20** e **Client40**. Selecione o **iniciar** ação para esses três projetos e deixe o resto definido como **nenhum**.  
  
4.  Clique em **Okey** e, em seguida, pressione F5 para executar o exemplo.
