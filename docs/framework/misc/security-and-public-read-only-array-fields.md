---
title: Segurança e campos de matriz públicos somente leitura
description: Leia por que você deve evitar o uso de campos públicos de matriz somente leitura para definir o comportamento de limite ou a segurança de seus aplicativos.
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 0a6a82c2c88fe61bd34c0accb831f018cf8702fc
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281427"
---
# <a name="security-and-public-read-only-array-fields"></a>Segurança e campos de matriz públicos somente leitura
Nunca use campos de matriz pública somente leitura de bibliotecas gerenciadas para definir o comportamento de limite ou a segurança de seus aplicativos porque campos de matriz pública somente leitura podem ser modificados.  
  
## <a name="remarks"></a>Comentários  

Algumas classes .NET incluem campos públicos somente leitura que contêm parâmetros de limite específicos da plataforma. Por exemplo, o <xref:System.IO.Path.InvalidPathChars> campo é uma matriz que descreve os caracteres que não são permitidos em uma cadeia de caracteres de caminho de arquivo. Muitos campos semelhantes estão presentes em todo o .NET.  
  
 Os valores de campos somente leitura públicos como <xref:System.IO.Path.InvalidPathChars> podem ser modificados pelo código ou código que compartilha o domínio do aplicativo do código.  Você não deve usar campos de matriz pública somente leitura como este para definir o comportamento de limite de seus aplicativos.  Se você fizer isso, o código mal-intencionado poderá alterar as definições de limite e usar seu código de maneiras inesperadas.  
  
 Na versão 2,0 e posteriores do .NET Framework, você deve usar métodos que retornam uma nova matriz em vez de campos de matriz pública.  Por exemplo, em vez de usar o <xref:System.IO.Path.InvalidPathChars> campo, você deve usar o <xref:System.IO.Path.GetInvalidPathChars%2A> método.  
  
 Observe que os tipos de .NET Framework não usam os campos públicos para definir tipos de limite internamente.  Em vez disso, o .NET Framework usa campos particulares separados.  A alteração dos valores desses campos públicos não altera o comportamento dos tipos de .NET Framework.  
  
## <a name="see-also"></a>Confira também

- [Diretrizes de codificação segura](../../standard/security/secure-coding-guidelines.md)
