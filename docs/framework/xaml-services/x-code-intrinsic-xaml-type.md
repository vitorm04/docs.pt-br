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
ms.openlocfilehash: 7bb78b05be7b3edc4471bc276010eabd92a07a14
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971841"
---
# <a name="xcode-intrinsic-xaml-type"></a>Tipo intrínseco x:Code (XAML)
Permite o posicionamento de código dentro de uma produção de XAML. Esse código também pode ser compilado por qualquer implementação do processador XAML que compila XAML ou à esquerda na produção para uso posterior, como de interpretação XAML por um tempo de execução.  
  
## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>Comentários  
 O código dentro de `x:Code` elemento de diretiva de XAML é ainda interpretada dentro do namespace XML geral e os namespaces XAML fornecidos. Portanto, é geralmente necessário incluir o código usado para `x:Code` dentro de um `CDATA` segmento.  
  
 `x:Code` não é permitida em todos os mecanismos de implantação possíveis de uma produção de XAML. O código deve ser compilado em estruturas específicas (por exemplo, WPF). Em outras estruturas, `x:Code` uso pode ser geralmente não permitido.  
  
 Para estruturas que permitem gerenciado `x:Code` de conteúdo, o compilador de idioma correto a ser usado para `x:Code` conteúdo é determinado pelas configurações e destinos do projeto que é usado para compilar o aplicativo.  
  
## <a name="wpf-usage-notes"></a>Notas de uso do WPF  
 Código declarado em `x:Code` para WPF tem várias limitações importantes:  
  
- O `x:Code` elemento de diretiva deve ser um elemento filho imediatos do elemento raiz da produção de XAML.  
  
- [Diretiva X:Class](x-class-directive.md) deve ser fornecido no elemento root pai.  
  
- O código é colocado dentro de `x:Code` será tratado pela compilação como dentro do escopo da classe parcial que já está sendo criado para a página XAML. Portanto, todo código que você definir deve ser membros ou variáveis de classe parcial.  
  
- Você não pode definir classes adicionais, além de aninhamento de uma classe dentro da classe parcial (aninhamento é permitido, mas não é comum porque as classes aninhadas não podem ser referenciadas em XAML). Namespaces CLR que não seja o namespace que é usado para a classe parcial existente não pode ser definida ou adicionado ao.  
  
- Referências a entidades de código fora do namespace CLR de classe parcial devem ser totalmente qualificadas. Se os membros que estão sendo declarados são substituições para os membros de classe parcial substituível, isso deve ser especificado com a palavra-chave específicas de idioma de substituição. Se os membros declarados em `x:Code` escopo estão em conflito com os membros da classe parcial, criada a partir do XAML, de forma que o compilador relatará o conflito, o arquivo XAML não é possível compilar ou carregar.  
  
## <a name="see-also"></a>Consulte também

- [Diretiva x:Class](x-class-directive.md)
- [Code-behind e XAML no WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [Visão geral de XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
