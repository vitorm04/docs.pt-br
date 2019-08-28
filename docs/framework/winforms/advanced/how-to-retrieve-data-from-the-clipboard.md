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
ms.openlocfilehash: ca24615049abcc145698c033f31e6c98a38253bf
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040564"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>Como: recuperar dados da área de transferência

A <xref:System.Windows.Forms.Clipboard> classe fornece métodos que você pode usar para interagir com o recurso de área de transferência do sistema operacional Windows. Muitos aplicativos usam a Área de Transferência como um repositório temporário para dados. Por exemplo, processadores globais usam a Área de Transferência durante operações de cortar e colar. A Área de Transferência também é útil para transferir informações de um aplicativo para outro.

Alguns aplicativos armazenam dados na Área de Transferência em vários formatos para aumentar o número de outros aplicativos que potencialmente podem usar os dados. Um formato da Área de Transferência é uma cadeia de caracteres que identifica o formato. Um aplicativo que usa o formato identificado pode recuperar os dados associados na Área de Transferência. A <xref:System.Windows.Forms.DataFormats> classe fornece nomes de formato predefinidos para seu uso. Você também pode usar seus próprios nomes de formato ou usar o tipo de um objeto como seu formato. Para obter informações sobre como adicionar dados à área de [transferência, consulte Como: Adicione dados à área de](how-to-add-data-to-the-clipboard.md)transferência.

Para determinar se a área de transferência contém dados em um formato específico, use um `Contains`dos métodos *Format* ou <xref:System.Windows.Forms.Clipboard.GetData%2A> o método. Para recuperar dados da área de transferência, use um dos `Get`métodos *Format* ou o <xref:System.Windows.Forms.Clipboard.GetData%2A> método. Esses métodos são novos no .NET Framework 2,0.

Para acessar dados da área de transferência usando versões anteriores à .NET Framework 2,0, use o <xref:System.Windows.Forms.Clipboard.GetDataObject%2A?displayProperty=nameWithType> método e chame os métodos do retornado. <xref:System.Windows.Forms.IDataObject> Para determinar se um determinado formato está disponível no objeto retornado, por exemplo, chame o <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> método.

> [!NOTE]
> Todos os aplicativos do Windows compartilham a Área de Transferência do sistema. Portanto, os conteúdos estão sujeito a alterações quando você muda para outro aplicativo.
>
> A <xref:System.Windows.Forms.Clipboard> classe só pode ser usada em threads definidos como o modo STA (single thread apartment). Para usar essa classe, verifique se o `Main` método está marcado com o <xref:System.STAThreadAttribute> atributo.

### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>Recuperar dados da Área de Transferência em um único formato comum

1. Use o <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>método <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, ou <xref:System.Windows.Forms.Clipboard.GetText%2A> . Opcionalmente, use os métodos `Contains`*Formato* correspondentes primeiro para determinar se os dados estão disponíveis em um formato específico. Esses métodos estão disponíveis apenas no .NET Framework 2,0.

    [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
    [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]

### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>Recuperar dados da Área de Transferência em um formato personalizado

1. Use o <xref:System.Windows.Forms.Clipboard.GetData%2A> método com um nome de formato personalizado. Esse método está disponível somente no .NET Framework 2,0.

    Você também pode usar nomes de formato predefinidos com o <xref:System.Windows.Forms.Clipboard.SetData%2A> método. Para obter mais informações, consulte <xref:System.Windows.Forms.DataFormats>.

    [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
    [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>Recuperar dados da Área de Transferência em vários formatos

1. Use o método <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>. Você deve usar esse método para recuperar dados da área de transferência em versões anteriores à .NET Framework 2,0.

    [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
    [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

## <a name="see-also"></a>Consulte também

- [Operações do Tipo "Arrastar e Soltar" e Suporte à Área de Transferência](drag-and-drop-operations-and-clipboard-support.md)
- [Como: Adicionar dados à área de transferência](how-to-add-data-to-the-clipboard.md)
