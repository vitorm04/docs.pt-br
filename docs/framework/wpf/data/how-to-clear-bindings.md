---
title: "Como limpar associações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af45d504eb4e7d45808f787925a90c8e0ed19476
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-clear-bindings"></a>Como limpar associações
Este exemplo mostra como limpar as associações de um objeto.  
  
## <a name="example"></a>Exemplo  
 Para limpar uma associação de uma propriedade individual em um objeto, chame <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> conforme mostrado no exemplo a seguir. O exemplo a seguir remove a associação do <xref:System.Windows.Controls.TextBlock.TextProperty> de *mytext*, um <xref:System.Windows.Controls.TextBlock> objeto.  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 Limpar a associação remove a associação para que o valor da propriedade de dependência é alterado para tudo o que teria sido sem a associação. Esse valor pode ser um valor padrão, um valor herdado ou um valor de uma associação de modelo de dados.  
  
 Para limpar as associações de todas as propriedades possíveis em um objeto, use <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Data.BindingOperations>  
 [Visão geral da vinculação de dados](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
