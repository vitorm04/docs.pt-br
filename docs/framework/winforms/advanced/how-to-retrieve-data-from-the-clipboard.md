---
title: 'Como: recuperar dados da área de transferência'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
ms.openlocfilehash: 868afc36f08571d16285d0df52f6d1cad8c9c7a6
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348214"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>Como: recuperar dados da área de transferência
O <xref:System.Windows.Forms.Clipboard> classe fornece métodos que você pode usar para interagir com o recurso de área de transferência do sistema operacional Windows. Muitos aplicativos usam a Área de Transferência como um repositório temporário para dados. Por exemplo, processadores globais usam a Área de Transferência durante operações de cortar e colar. A Área de Transferência também é útil para transferir informações de um aplicativo para outro.  
  
 Alguns aplicativos armazenam dados na Área de Transferência em vários formatos para aumentar o número de outros aplicativos que potencialmente podem usar os dados. Um formato da Área de Transferência é uma cadeia de caracteres que identifica o formato. Um aplicativo que usa o formato identificado pode recuperar os dados associados na Área de Transferência. O <xref:System.Windows.Forms.DataFormats> classe fornece os nomes de formato predefinidos para seu uso. Você também pode usar seus próprios nomes de formato ou usar o tipo de um objeto como seu formato. Para obter informações sobre como adicionar dados à área de transferência, consulte [como: Adicionar dados à área de transferência](how-to-add-data-to-the-clipboard.md).  
  
 Para determinar se a área de transferência contém dados em um formato específico, use um dos `Contains` *formato* métodos ou o <xref:System.Windows.Forms.Clipboard.GetData%2A> método. Para recuperar dados da área de transferência, use um dos `Get` *formato* métodos ou o <xref:System.Windows.Forms.Clipboard.GetData%2A> método. Esses métodos são novos no .NET Framework 2.0.  
  
 Para acessar dados da área de transferência usando versões anteriores ao .NET Framework 2.0, use o <xref:System.Windows.Forms.Clipboard.GetDataObject%2A?displayProperty=nameWithType> método e chamar os métodos de retornado <xref:System.Windows.Forms.IDataObject>. Para determinar se um determinado formato está disponível no objeto retornado, por exemplo, chamar o <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> método.  
  
> [!NOTE]
>  Todos os aplicativos do Windows compartilham a Área de Transferência do sistema. Portanto, os conteúdos estão sujeito a alterações quando você muda para outro aplicativo.  
>   
>  O <xref:System.Windows.Forms.Clipboard> classe só pode ser usada em threads configurados para modo do único thread apartment (STA). Para usar essa classe, certifique-se de que seu `Main` método é marcado com o <xref:System.STAThreadAttribute> atributo.  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>Recuperar dados da Área de Transferência em um único formato comum  
  
1. Use o <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, ou <xref:System.Windows.Forms.Clipboard.GetText%2A> método. Opcionalmente, use os métodos `Contains`*Formato* correspondentes primeiro para determinar se os dados estão disponíveis em um formato específico. Esses métodos estão disponíveis apenas no .NET Framework 2.0.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>Recuperar dados da Área de Transferência em um formato personalizado  
  
1. Use o <xref:System.Windows.Forms.Clipboard.GetData%2A> método com um nome de formato personalizado. Esse método está disponível apenas no .NET Framework 2.0.  
  
     Você também pode usar nomes de formato predefinidos com o <xref:System.Windows.Forms.Clipboard.SetData%2A> método. Para obter mais informações, consulte <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>Recuperar dados da Área de Transferência em vários formatos  
  
1. Use o método <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>. Você deve usar esse método para recuperar dados da área de transferência em versões anteriores ao .NET Framework 2.0.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Consulte também

- [Operações do Tipo "Arrastar e Soltar" e Suporte à Área de Transferência](drag-and-drop-operations-and-clipboard-support.md)
- [Como: Adicionar dados à área de transferência](how-to-add-data-to-the-clipboard.md)
