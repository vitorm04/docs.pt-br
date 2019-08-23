---
title: Segurança e campos de matriz públicos somente leitura
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d36009fa4fc7b9299708768fe34a75f1fde6797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910732"
---
# <a name="security-and-public-read-only-array-fields"></a>Segurança e campos de matriz públicos somente leitura
Nunca use campos de matriz pública somente leitura de bibliotecas gerenciadas para definir o comportamento de limite ou a segurança de seus aplicativos porque campos de matriz pública somente leitura podem ser modificados.  
  
## <a name="remarks"></a>Comentários  
 Algumas classes do .NET Framework incluem campos públicos somente leitura que contêm parâmetros de limite específicos da plataforma.  Por exemplo, o <xref:System.IO.Path.InvalidPathChars> campo é uma matriz que descreve os caracteres que não são permitidos em uma cadeia de caracteres de caminho de arquivo.  Muitos campos semelhantes estão presentes durante o .NET Framework.  
  
 Os valores de campos somente leitura públicos como <xref:System.IO.Path.InvalidPathChars> podem ser modificados pelo código ou código que compartilha o domínio do aplicativo do código.  Você não deve usar campos de matriz pública somente leitura como este para definir o comportamento de limite de seus aplicativos.  Se você fizer isso, o código mal-intencionado poderá alterar as definições de limite e usar seu código de maneiras inesperadas.  
  
 Na versão 2,0 e posteriores do .NET Framework, você deve usar métodos que retornam uma nova matriz em vez de campos de matriz pública.  Por exemplo, em vez de usar <xref:System.IO.Path.InvalidPathChars> o campo, você deve usar <xref:System.IO.Path.GetInvalidPathChars%2A> o método.  
  
 Observe que os tipos de .NET Framework não usam os campos públicos para definir tipos de limite internamente.  Em vez disso, o .NET Framework usa campos particulares separados.  A alteração dos valores desses campos públicos não altera o comportamento dos tipos de .NET Framework.  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de codificação segura](../../standard/security/secure-coding-guidelines.md)
