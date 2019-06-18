---
title: 'Como: ler metadados de imagem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 3266724503960b8b45cd134dfa5b007a58d578fa
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169809"
---
# <a name="how-to-read-image-metadata"></a>Como: ler metadados de imagem
Alguns arquivos de imagem contêm metadados que você pode ler para determinar os recursos da imagem. Por exemplo, uma fotografia digital pode conter metadados que você pode ler para determinar a marca e modelo da câmera usada para capturar a imagem. Com o [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], você pode ler os metadados existentes e escrever novos metadados para os arquivos de imagem.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] armazena um item individual de metadados em um <xref:System.Drawing.Imaging.PropertyItem> objeto. Você pode ler o <xref:System.Drawing.Image.PropertyItems%2A> propriedade de um <xref:System.Drawing.Image> objeto para recuperar todos os metadados de um arquivo. O <xref:System.Drawing.Image.PropertyItems%2A> propriedade retorna uma matriz de <xref:System.Drawing.Imaging.PropertyItem> objetos.  
  
 Um <xref:System.Drawing.Imaging.PropertyItem> objeto tem as seguintes quatro propriedades: `Id`, `Value`, `Len`, e `Type`.  
  
## <a name="id"></a>Id  
 Uma marca que identifica o item de metadados. Alguns valores que podem ser atribuídos a <xref:System.Drawing.Imaging.PropertyItem.Id%2A> são mostrados na tabela a seguir.  
  
|Valor hexadecimal|Descrição|  
|-----------------------|-----------------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Título da imagem<br /><br /> Fabricante do equipamento<br /><br /> Modelo do equipamento<br /><br /> ExifDTOriginal<br /><br /> Tempo de exposição de Exif<br /><br /> Tabela de luminância<br /><br /> Tabela de crominância|  
  
## <a name="value"></a>Valor  
 Uma matriz de valores. O formato dos valores é determinado pelo <xref:System.Drawing.Imaging.PropertyItem.Type%2A> propriedade.  
  
## <a name="len"></a>Len  
 O comprimento (em bytes) da matriz de valores apontada pelo <xref:System.Drawing.Imaging.PropertyItem.Value%2A> propriedade.  
  
## <a name="type"></a>Tipo  
 O tipo de dados dos valores na matriz aponta para a propriedade `Value`. Os formatos indicados pelos valores de propriedade `Type` são mostrados na tabela a seguir  
  
|Valor numérico|Descrição|  
|-------------------|-----------------|  
|1|Um `Byte`|  
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
  
### <a name="description"></a>Descrição  
 O exemplo de código a seguir lê e exibe as sete partes dos metadados no arquivo `FakePhoto.jpg`. O segundo item de propriedade (índice 1) na lista tem <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (fabricante do equipamento) e <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (matriz de bytes codificados em ASCII). O exemplo de código exibe o valor desse item de propriedade.  
  
 O código produz uma saída semelhante à seguinte:  
 
```
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
  
### <a name="code"></a>Código  
 [!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos. Lidar com o formulário <xref:System.Windows.Forms.Control.Paint> eventos e cole este código no manipulador de eventos de pintura. Você deve substituir `FakePhoto.jpg` por um nome e caminho de imagem válidos no seu sistema e importar o namespace `System.Drawing.Imaging`.  
  
## <a name="see-also"></a>Consulte também

- [Imagens, bitmaps e metarquivos](images-bitmaps-and-metafiles.md)
- [Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos](working-with-images-bitmaps-icons-and-metafiles.md)
