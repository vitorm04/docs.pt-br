---
title: Tipo intrínseco x:Code (XAML)
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: 4da72ed630c1df001e3fd6c7e55f866b94c4d9b1
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071552"
---
# <a name="xcode-intrinsic-xaml-type"></a>Tipo intrínseco x:Code (XAML)
Permite a colocação de código dentro de uma produção XAML. Esse código pode ser compilado por qualquer implementação de processador XAML que compile XAML, ou deixado na produção XAML para usos posteriores, como interpretação por tempo de execução.

## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML

```xaml
<x:Code>
   // code instructions, usually enclosed by CDATA...
</x:Code>
```

## <a name="remarks"></a>Comentários

O código `x:Code` dentro do elemento de diretiva XAML ainda é interpretado dentro do espaço de nome XML geral e dos namespaces XAML fornecidos. Portanto, geralmente é necessário envolver o código `x:Code` usado `CDATA` para dentro de um segmento.

`x:Code`não é permitido para todos os mecanismos de implantação possíveis de uma produção XAML. Em frameworks específicos (por exemplo, WPF) o código deve ser compilado. Em outros quadros, `x:Code` o uso pode ser geralmente proibido.

Para estruturas que permitem `x:Code` conteúdo gerenciado, o compilador `x:Code` de idiomas correto para usar para conteúdo é determinado por configurações e metas do projeto de contenção que é usado para compilar o aplicativo.

## <a name="wpf-usage-notes"></a>Notas de uso do WPF

O código `x:Code` declarado dentro do WPF tem várias limitações notáveis:

- O `x:Code` elemento diretivo deve ser um elemento filho imediato do elemento raiz da produção XAML.

- [x:Diretiva de classe](xclass-directive.md) deve ser fornecida no elemento raiz pai.

- O código `x:Code` colocado dentro será tratado por compilação para estar dentro do escopo da classe parcial que já está sendo criada para essa página XAML. Portanto, todo o código que você define deve ser membros ou variáveis dessa classe parcial.

- Você não pode definir classes adicionais, exceto aninhando uma classe dentro da classe parcial (o aninhamento é permitido, mas não é típico porque classes aninhadas não podem ser referenciadas em XAML). Os namespaces clr que não sejam o namespace usado para a classe parcial existente não podem ser definidos ou adicionados.

- As referências a entidades de código fora do espaço de nome CLR de classe parcial devem ser totalmente qualificadas. Se os membros que estão sendo declarados forem substituídos pelos membros parcialmente da classe, isso deve ser especificado com a palavra-chave de substituição específica do idioma. Se os membros `x:Code` declarados em conflito de escopo com membros da classe parcial criados a partir do XAML, de tal forma que o compilador relatar o conflito, o arquivo XAML não poderá compilar ou carregar.

## <a name="see-also"></a>Confira também

- [Diretiva x:Class](xclass-directive.md)
- [Code-behind e XAML no WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [Visão geral de XAML (WPF)](../fundamentals/xaml.md)
