---
title: "Como recuperar dados da área de transferência"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c009efe743865896341da268bd14bf24158df46d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>Como recuperar dados da área de transferência
O <xref:System.Windows.Forms.Clipboard> classe fornece métodos que você pode usar para interagir com o recurso de área de transferência do sistema operacional Windows. Muitos aplicativos usam a Área de Transferência como um repositório temporário para dados. Por exemplo, processadores globais usam a Área de Transferência durante operações de cortar e colar. A Área de Transferência também é útil para transferir informações de um aplicativo para outro.  
  
 Alguns aplicativos armazenam dados na Área de Transferência em vários formatos para aumentar o número de outros aplicativos que potencialmente podem usar os dados. Um formato da Área de Transferência é uma cadeia de caracteres que identifica o formato. Um aplicativo que usa o formato identificado pode recuperar os dados associados na Área de Transferência. O <xref:System.Windows.Forms.DataFormats> classe fornece os nomes de formato predefinidos para seu uso. Você também pode usar seus próprios nomes de formato ou usar o tipo de um objeto como seu formato. Para obter informações sobre como adicionar dados à Área de Transferência, consulte [Como adicionar dados à Área de Transferência](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md).  
  
 Para determinar se a área de transferência contém dados em um formato específico, use um do `Contains` *formato* métodos ou <xref:System.Windows.Forms.Clipboard.GetData%2A> método. Para recuperar dados da área de transferência, use um do `Get` *formato* métodos ou <xref:System.Windows.Forms.Clipboard.GetData%2A> método. Esses métodos são novos em [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
 Para acessar dados da área de transferência usando versões anteriores ao [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)], use o <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> método e chamar os métodos de retornado <xref:System.Windows.Forms.IDataObject>. Para determinar se um determinado formato está disponível no objeto retornado, por exemplo, chamar o <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> método.  
  
> [!NOTE]
>  Todos os aplicativos do Windows compartilham a Área de Transferência do sistema. Portanto, os conteúdos estão sujeito a alterações quando você muda para outro aplicativo.  
>   
>  O <xref:System.Windows.Forms.Clipboard> classe só pode ser usada em threads configurados para o modo single thread apartment (STA). Para usar essa classe, certifique-se de que seu `Main` método está marcado com o <xref:System.STAThreadAttribute> atributo.  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>Recuperar dados da Área de Transferência em um único formato comum  
  
1.  Use o <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, ou <xref:System.Windows.Forms.Clipboard.GetText%2A> método. Opcionalmente, use os métodos `Contains`*Formato* correspondentes primeiro para determinar se os dados estão disponíveis em um formato específico. Esses métodos estão disponíveis somente em [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>Recuperar dados da Área de Transferência em um formato personalizado  
  
1.  Use o <xref:System.Windows.Forms.Clipboard.GetData%2A> método com um nome de formato personalizado. Esse método está disponível apenas no [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].  
  
     Você também pode usar nomes de formato predefinidos com o <xref:System.Windows.Forms.Clipboard.SetData%2A> método. Para obter mais informações, consulte <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>Recuperar dados da Área de Transferência em vários formatos  
  
1.  Use o método <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>. Você deve usar esse método para recuperar dados da Área de Transferência em versões anteriores à [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Consulte também  
 [Operações do Tipo "Arrastar e Soltar" e Suporte à Área de Transferência](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [Como Adicionar Dados à Área de Transferência](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)
