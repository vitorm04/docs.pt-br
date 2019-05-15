---
title: 'Como: criar um arquivo ou uma pasta – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: 3163598de5d03bf1691379cddae031841b9865d6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595636"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>Como: criar um arquivo ou uma pasta (Guia de Programação em C#)
Você pode criar uma pasta no seu computador, criar uma subpasta, criar um arquivo na subpasta e gravar dados no arquivo programaticamente.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 Se a pasta já existir, <xref:System.IO.Directory.CreateDirectory%2A> não fará nada, e nenhuma exceção será gerada. No entanto, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> substituirá um arquivo existente por um novo. O exemplo usa uma instrução `if`-`else` para impedir que um arquivo existente seja substituído.  
  
 Fazendo as alterações a seguir no exemplo, você pode especificar diferentes resultados com base em se já existe um arquivo com um determinado nome. Se esse arquivo não existir, o código criará um. Se esse arquivo existir, o código acrescentará dados a esse arquivo.  
  
- Especifique um nome de arquivo não aleatório.  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- Substitua a instrução `if`-`else` pela instrução `using` no código a seguir.  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 Execute o exemplo várias vezes para verificar se os dados são adicionados ao arquivo a cada vez.  
  
 Para ver mais valores `FileMode` que você pode tentar, consulte <xref:System.IO.FileMode>.  
  
 As seguintes condições podem causar uma exceção:  
  
- O nome da pasta está malformado. Por exemplo, ele contém caracteres inválidos ou é somente um espaço em branco (classe <xref:System.ArgumentException>). Use a classe <xref:System.IO.Path> para criar nomes de caminho válidos.  
  
- A pasta pai da pasta a ser criada é somente leitura (classe <xref:System.IO.IOException>).  
  
- O nome da pasta é `null` (classe <xref:System.ArgumentNullException>).  
  
- O nome da pasta é longo demais (classe <xref:System.IO.PathTooLongException>).  
  
- O nome da pasta contém apenas dois-pontos, “:” (classe <xref:System.IO.PathTooLongException>).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Uma instância da classe <xref:System.Security.SecurityException> poderá ser gerada em situações de confiança parcial.  
  
 Se você não tiver permissão para criar a pasta, o exemplo gerará uma instância da classe <xref:System.UnauthorizedAccessException>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IO?displayProperty=nameWithType>
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Sistema de arquivos e o Registro (Guia de Programação em C#)](../../../csharp/programming-guide/file-system/index.md)
