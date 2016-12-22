---
title: "Estruturas e outros elementos de programa&#231;&#227;o (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "matrizes [Visual Basic], elementos de estrutura"
  - "estruturas aninhadas"
  - "objetos [Visual Basic], elementos de estrutura"
  - "procedimentos, estruturas como argumentos para"
  - "estruturas, matrizes"
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Estruturas e outros elementos de programa&#231;&#227;o (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode usar as estruturas em conjunto com matrizes, objetos e procedimentos, bem como entre si.  As interações usam a mesma sintaxe que esses elementos usam individualmente.  
  
> [!NOTE]
>  Você não pode inicializar qualquer um dos elementos de estrutura na declaração da estrutura.  Você pode atribuir valores somente para elementos de uma variável que foi declarada para ser de um tipo de estrutura.  
  
## Estruturas e Matrizes  
 Uma estrutura pode conter uma matriz, bem como um ou mais de seus elementos.  O exemplo a seguir ilustra isto:  
  
```vb#  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 Você acessa os valores de uma matriz em uma estrutura da mesma maneira que você acessa uma propriedade em um objeto.  O exemplo a seguir ilustra isto:  
  
```vb#  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 Você pode também declarar uma matriz de estruturas.  O exemplo a seguir ilustra isto:  
  
```vb#  
Dim allSystems(100) As systemInfo  
```  
  
 Você segue as mesmas regras para acessar os componentes dessa arquitetura de dados.  O exemplo a seguir ilustra isto:  
  
```vb#  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## Estruturas e Objetos  
 Uma estrutura pode conter um objeto, bem como um ou mais de seus elementos.  O exemplo a seguir ilustra isto:  
  
```vb#  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 Você deve usar um classe de objeto específica em tal declaração, em vez de `Object`.  
  
## Estruturas e Procedimentos  
 Você pode passar uma estrutura como um argumento de procedimento.  O exemplo a seguir ilustra isto:  
  
```vb#  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 O exemplo anterior passa a estrutura *por referência*, o que permite que o procedimento modifique seus elementos de modo que as alterações tenham efeito no código de chamada.  Se você deseja proteger uma estrutura contra tal modificação, passe\-a por valor.  
  
 Você também pode retornar uma estrutura a partir de um procedimento `Function`.  O exemplo a seguir ilustra isto:  
  
```vb#  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## Estruturas dentro de Estruturas  
 Estruturas podem conter outras estruturas.  O exemplo a seguir ilustra isto:  
  
```vb#  
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
  
```vb#  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 Você também pode usar essa técnica para encapsular uma estrutura definida em um módulo dentro de uma estrutura definida em um módulo diferente.  
  
 Estruturas podem conter outras estruturas a uma profundidade arbitrária.  
  
## Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Como declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Variáveis de estrutura](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)   
 [Estruturas e classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)