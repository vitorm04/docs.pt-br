---
title: 'Como: adicionar dados à área de transferência'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
ms.openlocfilehash: d4afcd6ce942d1cd2286e3f393ce61436821bb3a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955121"
---
# <a name="how-to-add-data-to-the-clipboard"></a>Como: adicionar dados à área de transferência
A <xref:System.Windows.Forms.Clipboard> classe fornece métodos que você pode usar para interagir com o recurso de área de transferência do sistema operacional Windows. Muitos aplicativos usam a Área de Transferência como um repositório temporário para dados. Por exemplo, processadores globais usam a Área de Transferência durante operações de cortar e colar. A Área de Transferência também é útil para transferir dados de um aplicativo para outro.  
  
 Quando você adiciona dados à Área de Transferência, você pode indicar o formato de dados para que outros aplicativos possam reconhecer os dados se puderem usar esse formato. Você também pode adicionar dados à Área de Transferência em vários formatos diferentes para aumentar o número de outros aplicativos que potencialmente podem usar os dados.  
  
 Um formato da Área de Transferência é uma cadeia de caracteres que identifica o formato para que um aplicativo que use esse formato possa recuperar os dados associados. A <xref:System.Windows.Forms.DataFormats> classe fornece nomes de formato predefinidos para seu uso. Você também pode usar seus próprios nomes de formato ou usar o tipo de um objeto como o formato.  
  
 Para adicionar dados à área de transferência em um ou vários formatos, use <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> o método. Você pode passar qualquer objeto para esse método, mas, para adicionar dados em vários formatos, é preciso primeiro adicionar os dados a um objeto separado projetado para funcionar com vários formatos. Normalmente, você adicionará seus dados a um <xref:System.Windows.Forms.DataObject>, mas poderá usar qualquer tipo que implemente a <xref:System.Windows.Forms.IDataObject> interface.  
  
 No .NET Framework 2,0, você pode adicionar dados diretamente à área de transferência usando novos métodos projetados para facilitar as tarefas básicas de área de transferência. Use esses métodos quando você trabalhar com os dados em um único formato comum, como texto.  
  
> [!NOTE]
> Todos os aplicativos baseados em Windows compartilham a Área de Transferência. Portanto, os conteúdos estão sujeito a alterações quando você muda para outro aplicativo.  
>   
>  A <xref:System.Windows.Forms.Clipboard> classe só pode ser usada em threads definidos como o modo STA (single thread apartment). Para usar essa classe, verifique se o `Main` método está marcado com o <xref:System.STAThreadAttribute> atributo.  
>   
>  Um objeto deve ser serializável para que seja colocado na Área de Transferência. Para tornar um tipo serializável, marque-o <xref:System.SerializableAttribute> com o atributo. Se você passar um objeto não serializável para um método de Área de Transferência, o método falhará sem lançar uma exceção. Para obter mais informações sobre serialização, consulte <xref:System.Runtime.Serialization>.  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>Para adicionar dados à Área de Transferência em um único formato comum  
  
1. Use o <xref:System.Windows.Forms.Clipboard.SetAudio%2A>método <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, ou <xref:System.Windows.Forms.Clipboard.SetText%2A> . Esses métodos estão disponíveis apenas no .NET Framework 2,0.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>Para adicionar dados à Área de Transferência em um formato personalizado  
  
1. Use o <xref:System.Windows.Forms.Clipboard.SetData%2A> método com um nome de formato personalizado. Esse método está disponível somente no .NET Framework 2,0.  
  
     Você também pode usar nomes de formato predefinidos com o <xref:System.Windows.Forms.Clipboard.SetData%2A> método. Para obter mais informações, consulte <xref:System.Windows.Forms.DataFormats>.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>Para adicionar dados à Área de Transferência em vários formatos  
  
1. Use o <xref:System.Windows.Forms.Clipboard.SetDataObject%2A?displayProperty=nameWithType> método e passe um <xref:System.Windows.Forms.DataObject> que contenha seus dados. Você deve usar esse método para adicionar dados à área de transferência em versões anteriores à .NET Framework 2,0.  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>Consulte também

- [Operações do Tipo "Arrastar e Soltar" e Suporte à Área de Transferência](drag-and-drop-operations-and-clipboard-support.md)
- [Como: Recuperar dados da área de transferência](how-to-retrieve-data-from-the-clipboard.md)
