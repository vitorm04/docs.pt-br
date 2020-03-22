---
title: Estruturas e outros elementos de programação
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: 73d3f999e95c484dff3f5409f2cdb9032b64fe38
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266853"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>Estruturas e outros elementos de programação (Visual Basic)
Você pode usar estruturas em conjunto com matrizes, objetos e procedimentos, bem como entre si. As interações usam a mesma sintaxe que esses elementos usam individualmente.  
  
> [!NOTE]
> Você não pode inicializar nenhum dos elementos estruturais na declaração de estrutura. Você pode atribuir valores apenas a elementos de uma variável que foi declarada como sendo de um tipo de estrutura.  
  
## <a name="structures-and-arrays"></a>Estruturas e Matrizes  
 Uma estrutura pode conter uma matriz como um ou mais de seus elementos. O exemplo a seguir ilustra isto.  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure
```  
  
 Você acessa os valores de uma matriz dentro de uma estrutura da mesma forma que você acessa uma propriedade em um objeto. O exemplo a seguir ilustra isto.  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 Você também pode declarar uma matriz de estruturas. O exemplo a seguir ilustra isto.  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 Você segue as mesmas regras para acessar os componentes desta arquitetura de dados. O exemplo a seguir ilustra isto.  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>Estruturas e Objetos  
 Uma estrutura pode conter um objeto como um ou mais de seus elementos. O exemplo a seguir ilustra isto.  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 Você deve usar uma classe de objeto `Object`específica em tal declaração, em vez de .  
  
## <a name="structures-and-procedures"></a>Estruturas e Procedimentos  
 Você pode passar uma estrutura como argumento de procedimento. O exemplo a seguir ilustra isto.  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 O exemplo anterior passa a estrutura *por referência,* o que permite que o procedimento modifique seus elementos para que as alterações surtam efeito no código de chamada. Se você quiser proteger uma estrutura contra tal modificação, passe-a por valor.  
  
 Você também pode retornar `Function` uma estrutura de um procedimento. O exemplo a seguir ilustra isto.  
  
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
  
## <a name="structures-within-structures"></a>Estruturas dentro das estruturas  
 Estruturas podem conter outras estruturas. O exemplo a seguir ilustra isto.  
  
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
  
 Estruturas podem conter outras estruturas a uma profundidade arbitrária.  
  
## <a name="see-also"></a>Confira também

- [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Solução de problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Como declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Variáveis de Estrutura](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [Estruturas e Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
