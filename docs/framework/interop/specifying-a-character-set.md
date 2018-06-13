---
title: Especificando um conjunto de caracteres
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- platform invoke, attribute fields
- attribute fields in platform invoke, CharSet
- CharSet field
ms.assetid: a8347eb1-295f-46b9-8a78-63331f9ecc50
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1016a0c63a85919764271e01771ff8192341725c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398229"
---
# <a name="specifying-a-character-set"></a>Especificando um conjunto de caracteres
O campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> controla o marshaling de cadeia de caracteres e determina como a invocação de plataforma localiza os nomes de função em uma DLL. Este tópico descreve os dois comportamentos.  
  
 Algumas APIs exportam duas versões de funções que usam argumentos de cadeia de caracteres: estreita (ANSI) e larga (Unicode). A API do Win32, por exemplo, inclui os seguintes nomes do ponto de entrada para a função **MessageBox**:  
  
-   **MessageBoxA**  
  
     Fornece a formatação ANSI de caracteres de 1 byte, diferenciada por um “A” acrescentado ao nome do ponto de entrada. As chamadas a **MessageBoxA** sempre realizam marshaling das cadeias de caracteres no formato ANSI, comportamento comum nas plataformas Windows 95 e Windows 98.  
  
-   **MessageBoxW**  
  
     Fornece a formatação Unicode de caracteres de 2 bytes, diferenciada por um “W” acrescentado ao nome do ponto de entrada. As chamadas a **MessageBoxW** sempre realizam marshaling das cadeias de caracteres no formato Unicode, comportamento comum nas plataformas Windows NT, Windows 2000 e Windows XP.  
  
## <a name="string-marshaling-and-name-matching"></a>Marshaling de cadeia de caracteres e correspondência de nomes  
 O campo **CharSet** aceita os seguintes valores:  
  
 **CharSet.Ansi** (valor padrão)  
  
-   Marshaling de cadeia de caracteres  
  
     A invocação de plataforma realiza marshaling das cadeias de caracteres de seu formato gerenciado (Unicode) para o formato ANSI.  
  
-   Correspondência de nomes  
  
     Quando o campo <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> é **true**, que é o padrão no [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], a invocação de plataforma procura somente o nome especificado. Por exemplo, se você especificar **MessageBox**, a invocação de plataforma procurará **MessageBox** e falhará quando não conseguir localizar a ortografia exata.  
  
     Quando o campo **ExactSpelling** é **false**, que é o padrão no C++ e no C#, a invocação de plataforma procura o alias não danificado primeiro (**MessageBox**) e, em seguida, o nome danificado (**MessageBoxA**), se o alias não danificado não é encontrado. Observe que o comportamento de correspondência de nomes do ANSI é diferente do comportamento de correspondência de nomes do Unicode.  
  
 **CharSet.Unicode**  
  
-   Marshaling de cadeia de caracteres  
  
     A invocação de plataforma copia as cadeias de caracteres de seu formato gerenciado (Unicode) para o formato Unicode.  
  
-   Correspondência de nomes  
  
     Quando o campo **ExactSpelling** é **true**, que é o padrão no [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], a invocação de plataforma procura somente o nome especificado. Por exemplo, se você especificar **MessageBox**, a invocação de plataforma procurará **MessageBox** e falhará se não conseguir localizar a ortografia exata.  
  
     Quando o campo **ExactSpelling** é **false**, que é o padrão no C++ e no C#, a invocação de plataforma procura o nome danificado primeiro (**MessageBoxW**) e, em seguida, o alias não danificado (**MessageBox**), se o nome danificado não é encontrado. Observe que o comportamento de correspondência de nomes do Unicode é diferente do comportamento de correspondência de nomes do ANSI.  
  
 **CharSet.Auto**  
  
-   A invocação de plataforma escolhe entre os formatos ANSI e Unicode em tempo de execução, com base na plataforma de destino.  
  
## <a name="specifying-a-character-set-in-visual-basic"></a>Especificando um conjunto de caracteres no Visual Basic  
 O exemplo a seguir declara a função **MessageBox** três vezes, cada vez com um comportamento diferente do conjunto de caracteres. É possível especificar o comportamento do conjunto de caracteres no Visual Basic adicionando a palavra-chave **Ansi**, **Unicode** ou **Auto** à instrução de declaração.  
  
 Se você omitir a palavra-chave do conjunto de caracteres, como é feito na primeira instrução de declaração, o campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> usará como padrão o conjunto de caracteres ANSI. A segunda e a terceira instruções no exemplo especificam explicitamente um conjunto de caracteres com uma palavra-chave.  
  
```vb  
Imports System.Runtime.InteropServices  
  
Public Class Win32  
   Declare Function MessageBoxA Lib "user32.dll"(ByVal hWnd As Integer, _  
       ByVal txt As String, ByVal caption As String, _  
       ByVal Typ As Integer) As Integer  
  
   Declare Unicode Function MessageBoxW Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
  
   Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, ByVal txt As String, _  
        ByVal caption As String, ByVal Typ As Integer) As Integer  
End Class  
```  
  
## <a name="specifying-a-character-set-in-c-and-c"></a>Especificando um conjunto de caracteres no C# e no C++  
 O campo <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> identifica o conjunto de caracteres subjacente como ANSI ou Unicode. O conjunto de caracteres controla como deve ser realizado o marshaling dos argumentos de cadeia de caracteres para um método. Use um dos seguintes formatos para indicar o conjunto de caracteres:  
  
```csharp  
[DllImport("dllname", CharSet=CharSet.Ansi)]  
[DllImport("dllname", CharSet=CharSet.Unicode)]  
[DllImport("dllname", CharSet=CharSet.Auto)]  
```  
  
```cpp  
[DllImport("dllname", CharSet=CharSet::Ansi)]  
[DllImport("dllname", CharSet=CharSet::Unicode)]  
[DllImport("dllname", CharSet=CharSet::Auto)]  
```  
  
 O exemplo a seguir mostra três definições gerenciadas da função **MessageBox** atribuída para especificar um conjunto de caracteres. Na primeira definição, por sua omissão, o campo **CharSet** usa como padrão o conjunto de caracteres ANSI.  
  
```csharp  
[DllImport("user32.dll")]  
    public static extern int MessageBoxA(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Unicode)]  
    public static extern int MessageBoxW(int hWnd, String text,   
        String caption, uint type);  
[DllImport("user32.dll", CharSet=CharSet.Auto)]  
    public static extern int MessageBox(int hWnd, String text,   
        String caption, uint type);  
```  
  
```cpp  
typedef void* HWND;  
  
//Can use MessageBox or MessageBoxA.  
[DllImport("user32")]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Can use MessageBox or MessageBoxW.  
[DllImport("user32", CharSet=CharSet::Unicode)]  
extern "C" int MessageBoxW(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
  
//Must use MessageBox.  
[DllImport("user32", CharSet=CharSet::Auto)]  
extern "C" int MessageBox(HWND hWnd,  
                          String* pText,  
                          String* pCaption,  
                          unsigned int uType);  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [Criando protótipos em código gerenciado](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [Exemplos de invocação de plataforma](../../../docs/framework/interop/platform-invoke-examples.md)  
 [Marshaling de dados com a invocação de plataforma](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)
