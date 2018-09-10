---
title: '#pragma (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 5ae397cc61e0c6b58ed2079369131ebb7e352eae
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43747477"
---
# <a name="pragma-c-reference"></a>#pragma (Referência de C#)
O `#pragma` fornece ao compilador instruções especiais para a compilação do arquivo no qual ele é exibido. O compilador deve dar suporte às instruções. Em outras palavras, não é possível usar `#pragma` para criar instruções personalizadas de pré-processamento. O compilador Microsoft C# dá suporte a estas duas `#pragma` instruções:  
  
 [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [#pragma checksum](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pragma-name`  
 O nome de um pragma reconhecido.  
  
 `pragma-arguments`  
 Argumentos específicos do pragma.  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Diretivas do pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)  
- [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
- [#pragma checksum](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
