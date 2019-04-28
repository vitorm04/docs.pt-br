---
title: Segurança e campos de matriz públicos somente leitura
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19b5ad73150697c1442056642a1b11d504ecc426
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61869740"
---
# <a name="security-and-public-read-only-array-fields"></a>Segurança e campos de matriz públicos somente leitura
Nunca use campos de matriz públicos somente leitura de bibliotecas gerenciadas para definir o comportamento de limite ou a segurança dos seus aplicativos, como campos de matriz públicos somente leitura podem ser modificados.  
  
## <a name="remarks"></a>Comentários  
 Algumas classes do .NET framework incluem campos públicos somente leitura que contenham parâmetros de limite específico da plataforma.  Por exemplo, o <xref:System.IO.Path.InvalidPathChars> campo é uma matriz que descreve os caracteres que não são permitidos em uma cadeia de caracteres de caminho de arquivo.  Muitos campos similares estão presentes em todo o .NET Framework.  
  
 Os valores de campos públicos de somente leitura como <xref:System.IO.Path.InvalidPathChars> pode ser modificado pelo seu código ou o código que compartilha o domínio de aplicativo do seu código.  Você não deve usar campos de matriz públicos somente leitura como este para definir o comportamento de limite de seus aplicativos.  Se você fizer isso, o código mal-intencionado pode alterar as definições de limite e usar seu código de maneiras inesperadas.  
  
 Na versão 2.0 e posterior do .NET Framework, você deve usar os métodos que retornam uma nova matriz em vez de usar campos de matriz públicos.  Por exemplo, em vez de usar o <xref:System.IO.Path.InvalidPathChars> campo, você deve usar o <xref:System.IO.Path.GetInvalidPathChars%2A> método.  
  
 Observe que os tipos do .NET Framework não usam os campos públicos para definir tipos de limites internamente.  Em vez disso, o .NET Framework usa campos particulares separados.  Alterando os valores desses campos públicos não altera o comportamento de tipos do .NET Framework.  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de codificação segura](../../../docs/standard/security/secure-coding-guidelines.md)
