---
title: '#pragma – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
ms.openlocfilehash: 3bd62364aeae0f21715711324655ef7d00d88afc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712449"
---
# <a name="pragma-c-reference"></a>#pragma (Referência de C#)
O `#pragma` fornece ao compilador instruções especiais para a compilação do arquivo no qual ele é exibido. O compilador deve dar suporte às instruções. Em outras palavras, não é possível usar `#pragma` para criar instruções personalizadas de pré-processamento. O compilador Microsoft C# dá suporte a estas duas `#pragma` instruções:  
  
 [#pragma warning](./preprocessor-pragma-warning.md)  
  
 [#pragma soma de verificação](./preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
## <a name="parameters"></a>parâmetros  
 `pragma-name`  
 O nome de um pragma reconhecido.  
  
 `pragma-arguments`  
 Argumentos específicos do pragma.  
  
## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [C# Diretivas de pré-processador](./index.md)
- [#pragma warning](./preprocessor-pragma-warning.md)
- [#pragma soma de verificação](./preprocessor-pragma-checksum.md)
