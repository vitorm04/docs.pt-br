---
title: Segurança e campos de matriz públicos somente leitura
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 2df4acc0606e4fe8fccee4a8acc6ab744dcbbb71
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452702"
---
# <a name="security-and-public-read-only-array-fields"></a>Segurança e campos de matriz públicos somente leitura
Nunca use campos de matriz pública somente leitura de bibliotecas gerenciadas para definir o comportamento de limite ou a segurança de seus aplicativos porque campos de matriz pública somente leitura podem ser modificados.  
  
## <a name="remarks"></a>Comentários  

Algumas classes .NET incluem campos públicos somente leitura que contêm parâmetros de limite específicos da plataforma. Por exemplo, o campo <xref:System.IO.Path.InvalidPathChars> é uma matriz que descreve os caracteres que não são permitidos em uma cadeia de caracteres de caminho de arquivo. Muitos campos semelhantes estão presentes em todo o .NET.  
  
 Os valores de campos somente leitura públicos como <xref:System.IO.Path.InvalidPathChars> podem ser modificados pelo código ou código que compartilha o domínio do aplicativo do seu código.  Você não deve usar campos de matriz pública somente leitura como este para definir o comportamento de limite de seus aplicativos.  Se você fizer isso, o código mal-intencionado poderá alterar as definições de limite e usar seu código de maneiras inesperadas.  
  
 Na versão 2,0 e posteriores do .NET Framework, você deve usar métodos que retornam uma nova matriz em vez de campos de matriz pública.  Por exemplo, em vez de usar o campo <xref:System.IO.Path.InvalidPathChars>, você deve usar o método <xref:System.IO.Path.GetInvalidPathChars%2A>.  
  
 Observe que os tipos de .NET Framework não usam os campos públicos para definir tipos de limite internamente.  Em vez disso, o .NET Framework usa campos particulares separados.  A alteração dos valores desses campos públicos não altera o comportamento dos tipos de .NET Framework.  
  
## <a name="see-also"></a>Confira também

- [Diretrizes de codificação segura](../../standard/security/secure-coding-guidelines.md)
