---
title: "#<a name=\"pragma-warning-c-reference\"></a>pragma warning (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#pragma warning'
helpviewer_keywords: '#pragma warning [C#]'
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5330b448dc2b328992b2d29699557d20df56dee4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-warning-c-reference"></a>#pragma warning (Referência de C#)
O `#pragma warning` pode habilitar ou desabilitar determinados avisos.  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `warning-list`  
 Uma lista de números de aviso separada por vírgulas. O prefixo "CS" é opcional.  
  
 Quando não houver números de aviso especificados, o `disable` desabilita todos os avisos e o `restore` habilita todos os avisos.  
  
> [!NOTE]
>  Para localizar números de aviso no Visual Studio, compile o projeto e, em seguida, procure os números de aviso na janela de **Saída**.  
  
## <a name="example"></a>Exemplo  
  
```csharp
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, CS3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore CS3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Diretivas do pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [Erros do Compilador do C#](../../../csharp/language-reference/compiler-messages/index.md)
