---
title: '#pragma – Referência de C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 65ca38ff6993117b6ed9f716d4ac93ba2d4a9ddf
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605661"
---
# <a name="pragma-c-reference"></a>#pragma (Referência de C#)
O `#pragma` fornece ao compilador instruções especiais para a compilação do arquivo no qual ele é exibido. O compilador deve dar suporte às instruções. Em outras palavras, não é possível usar `#pragma` para criar instruções personalizadas de pré-processamento. O compilador Microsoft C# dá suporte a estas duas `#pragma` instruções:  
  
 [#pragma warning](./preprocessor-pragma-warning.md)  
  
 [#pragma checksum](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pragma-name`  
 O nome de um pragma reconhecido.  
  
 `pragma-arguments`  
 Argumentos específicos do pragma.  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Diretivas do pré-processador do C#](./index.md)
- [#pragma warning](./preprocessor-pragma-warning.md)
- [#pragma checksum](./preprocessor-pragma-checksum.md)
