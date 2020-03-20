---
title: Como ler metadados de imagens
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: e2b56175e625281a920c390e5feb4238e3cb7f44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182519"
---
# <a name="how-to-read-image-metadata"></a>Como ler metadados de imagens

Alguns arquivos de imagem contêm metadados que você pode ler para determinar os recursos da imagem. Por exemplo, uma fotografia digital pode conter metadados que você pode ler para determinar a marca e modelo da câmera usada para capturar a imagem. Com o GDI+, você pode ler metadados existentes e também pode gravar novos metadados em arquivos de imagem.

O GDI+ armazena um pedaço <xref:System.Drawing.Imaging.PropertyItem> individual de metadados em um objeto. Você pode <xref:System.Drawing.Image.PropertyItems%2A> ler a <xref:System.Drawing.Image> propriedade de um objeto para recuperar todos os metadados de um arquivo. A <xref:System.Drawing.Image.PropertyItems%2A> propriedade retorna <xref:System.Drawing.Imaging.PropertyItem> uma série de objetos.

Um <xref:System.Drawing.Imaging.PropertyItem> objeto tem as `Id`seguintes quatro propriedades: , `Value`, `Len`e `Type`.

## <a name="id"></a>ID

Uma marca que identifica o item de metadados. Alguns valores que <xref:System.Drawing.Imaging.PropertyItem.Id%2A> podem ser atribuídos são mostrados na tabela a seguir:

|Valor hexadecimal|Descrição|
|-----------------------|-----------------|
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Título da imagem<br /><br /> Fabricante do equipamento<br /><br /> Modelo do equipamento<br /><br /> ExifDTOriginal<br /><br /> Tempo de exposição de Exif<br /><br /> Tabela de luminância<br /><br /> Tabela de crominância|

## <a name="value"></a>Valor

Uma matriz de valores. O formato dos valores <xref:System.Drawing.Imaging.PropertyItem.Type%2A> é determinado pela propriedade.

## <a name="len"></a>Len

O comprimento (em bytes) da matriz de <xref:System.Drawing.Imaging.PropertyItem.Value%2A> valores apontados pela propriedade.

## <a name="type"></a>Type

O tipo de dados dos valores na matriz aponta para a propriedade `Value`. Os formatos indicados `Type` pelos valores de propriedade são mostrados na tabela a seguir:

|Valor numérico|Descrição|
|-------------------|-----------------|
|1|Uma `Byte`|
|2|Uma matriz de objetos `Byte` codificados como ASCII|
|3|Um inteiro de 16 bits|
|4|Um inteiro de 32 bits|
|5|Uma matriz de dois objetos `Byte` que representam um número racional|
|6|Não usado|
|7|Indefinido|
|8|Não usado|
|9|`SLong`|
|10|`SRational`|

## <a name="example"></a>Exemplo
  
O exemplo de código a seguir lê e exibe as sete partes dos metadados no arquivo `FakePhoto.jpg`. O segundo item de propriedade (índice <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 1) da lista tem 0x010F (fabricante de equipamentos) e <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (matriz de bytes codificada por ASCII). O exemplo de código exibe o valor desse item de propriedade.

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

O código produz uma saída semelhante à seguinte:

```output
 Property Item 0
  
 id: 0x320
  
 type: 2

 length: 16 bytes
  
 Property Item 1
  
 id: 0x10f
  
 type: 2
  
 length: 17 bytes
  
 Property Item 2
  
 id: 0x110
  
 type: 2
  
 length: 7 bytes
  
 Property Item 3
  
 id: 0x9003
  
 type: 2
  
 length: 20 bytes
  
 Property Item 4
  
 id: 0x829a
  
 type: 5
  
 length: 8 bytes
  
 Property Item 5
  
 id: 0x5090
  
 type: 3
  
 length: 128 bytes
  
 Property Item 6
  
 id: 0x5091
  
 type: 3
  
 length: 128 bytes
  
 The equipment make is Northwind Camera.
 ```

## <a name="compiling-the-code"></a>Compilando o código

O exemplo anterior foi projetado para ser <xref:System.Windows.Forms.PaintEventArgs> `e`usado com formulários do <xref:System.Windows.Forms.Control.Paint> Windows e requer , o que é um parâmetro do manipulador de eventos. Manuseie <xref:System.Windows.Forms.Control.Paint> o evento do formulário e cole este código no manipulador de eventos de pintura. Você deve substituir `FakePhoto.jpg` por um nome e caminho de imagem válidos no seu sistema e importar o namespace `System.Drawing.Imaging`.

## <a name="see-also"></a>Confira também

- [Imagens, Bitmaps e Metaarquivos](images-bitmaps-and-metafiles.md)
- [Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos](working-with-images-bitmaps-icons-and-metafiles.md)
