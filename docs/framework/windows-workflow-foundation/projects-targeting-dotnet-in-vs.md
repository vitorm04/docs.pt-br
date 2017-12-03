---
title: Escrever projetos direcionar o.NET Framework 3.0 e os 3,5 no Visual Studio 2010
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6dc6657bad5cc11eaa723c733319673468749b79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="writing-projects-targeting-the-net-framework-30-and-35-in-visual-studio-2010"></a>Escrever projetos direcionar o.NET Framework 3.0 e os 3,5 no Visual Studio 2010
Você pode usar [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] para criar projetos que destinam-se a versão 3,0 ou 3,5 de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] . Este tópico descreve como fazer isso.  
  
> [!NOTE]
>  Ao adicionar atividades, certifique-se de que a versão desejada de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] está definida. Alterar a versão de destino de fluxo de trabalho depois que as atividades são adicionadas fará com que o fluxo de trabalho para validação de falha.  
  
> [!WARNING]
>  Abrindo fluxos de trabalho existentes em [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] que possuem. .NET Framework 3,5 atividades causará um erro em `this.SetValue()`. Para abrir projetos criados com as versões anteriores do. Framework .NET, primeiro abre um fluxo de trabalho em branco no designer e adicione a. Atividade líquida de Framework 3,5.  
  
## <a name="to-create-a-net-framework--30-or-35-project-with-visual-studio-2010"></a>Para criar o .NET Framework 3.0 ou 3,5 com um projeto Visual Studio 2010  
  
1.  Abra [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Selecione **arquivo**, **novo**, **projeto**.  
  
3.  Na lista suspensa na parte superior da caixa de diálogo, selecione a versão desejada de [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="to-upgrade-the-targeted-version-of-the-net-framework"></a>Para atualizar a versão de destino do.NET Framework  
  
1.  Clique com botão direito no projeto no Gerenciador de soluções e selecione **propriedades**.  
  
2.  No **Framework de destino** lista suspensa, selecione a versão desejada.
