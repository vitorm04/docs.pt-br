---
title: Estruturas e outros elementos de programação (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: a943bbdec617ba6c95685df3a4fcdb36b52def22
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819093"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>Estruturas e outros elementos de programação (Visual Basic)
Você pode usar as estruturas em conjunto com matrizes, objetos e procedimentos, bem como entre si. As interações usam a mesma sintaxe que esses elementos usam individualmente.  
  
> [!NOTE]
>  Não é possível inicializar todos os elementos de estrutura na declaração de estrutura. Você só pode atribuir valores aos elementos de uma variável que foi declarada para ser de um tipo de estrutura.  
  
## <a name="structures-and-arrays"></a>Estruturas e matrizes  
 Uma estrutura pode conter uma matriz como um ou mais dos seus elementos. O exemplo a seguir ilustra essa situação.  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 Você acessa os valores de uma matriz em uma estrutura da mesma maneira que você acessar uma propriedade em um objeto. O exemplo a seguir ilustra essa situação.  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 Você também pode declarar uma matriz de estruturas. O exemplo a seguir ilustra essa situação.  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 Você seguir as mesmas regras para acessar os componentes dessa arquitetura de dados. O exemplo a seguir ilustra essa situação.  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>Estruturas e objetos  
 Uma estrutura pode conter um objeto como um ou mais dos seus elementos. O exemplo a seguir ilustra essa situação.  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 Você deve usar uma classe de objeto específico na declaração, em vez de `Object`.  
  
## <a name="structures-and-procedures"></a>Estruturas e procedimentos  
 Você pode passar uma estrutura como um argumento de procedimento. O exemplo a seguir ilustra essa situação.  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 O exemplo anterior passa a estrutura *por referência*, que permite que o procedimento para modificar seus elementos para que as alterações tenham efeito no código de chamada. Se você quiser proteger uma estrutura contra tal modificação, passá-lo por valor.  
  
 Você também pode retornar uma estrutura de um `Function` procedimento. O exemplo a seguir ilustra essa situação.  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a>Estruturas dentro de estruturas  
 Estruturas podem conter outras estruturas. O exemplo a seguir ilustra essa situação.  
  
```vb  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 Você também pode usar essa técnica para encapsular uma estrutura definida em um módulo dentro de uma estrutura definida em um módulo diferente.  
  
 Estruturas podem conter outras estruturas em uma profundidade arbitrária.  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tipos de Dados Elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Tipos de Dados Compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Como: declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Variáveis de Estrutura](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [Estruturas e Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
