---
title: "#pragma (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma'
dev_langs:
- CSharp
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f616f96bf1060cc96f332077bc7a1a3858d572d2
ms.lasthandoff: 03/13/2017

---
# <a name="pragma-c-reference"></a>#pragma (Referência de C#)
O `#pragma` fornece ao compilador instruções especiais para a compilação do arquivo no qual ele é exibido. O compilador deve dar suporte às instruções. Em outras palavras, não é possível usar `#pragma` para criar instruções personalizadas de pré-processamento. O compilador Microsoft C# dá suporte a estas duas `#pragma` instruções:  
  
 [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [#pragma checksum](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```  
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pragma-name`  
 O nome de um pragma reconhecido.  
  
 `pragma-arguments`  
 Argumentos específicos do pragma.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Diretivas de pré-processador do C#](../../../csharp/language-reference/preprocessor-directives/index.md)   
 [Aviso #pragma](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)   
 [#pragma checksum](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
