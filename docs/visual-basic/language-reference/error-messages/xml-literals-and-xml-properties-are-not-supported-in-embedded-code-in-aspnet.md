---
title: Literais e propriedades de XML não são suportados em código inserido dentro do ASP.NET
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: d96386f8495685391203826fea85efba47c44951
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163253"
---
# <a name="bc31200-xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>BC31200: não há suporte para literais XML e propriedades XML no código inserido dentro do ASP.NET

Não há suporte para literais XML e propriedades XML no código inserido dentro de ASP.NET. Para usar recursos XML, mova o código para code-behind.

 Uma propriedade XML literal ou XML Axis é definida no código inserido ( `<%= =>` ) em um arquivo ASP.net.

 **ID do erro:** BC31200

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Mova o código que inclui o literal XML ou a propriedade de eixo XML para um arquivo code-behind ASP.NET.

## <a name="see-also"></a>Veja também

- [Literais XML](../xml-literals/index.md)
- [Propriedades do eixo XML](../xml-axis/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
