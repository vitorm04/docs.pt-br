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
ms.openlocfilehash: 92be0b3b0fd1212c4254a449f902b85e998aa148
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="xcode-intrinsic-xaml-type"></a>Tipo intrínseco x:Code (XAML)
Permite que o posicionamento de código dentro de uma produção XAML. Esse código pode ser compilado ou por qualquer implementação de processador XAML que compila XAML ou à esquerda na produção XAML para uso posterior, como interpretação por um tempo de execução.  
  
## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>Comentários  
 O código dentro do `x:Code` elemento de diretiva XAML é ainda interpretado dentro do namespace XML geral e os namespaces XAML fornecidos. Portanto, é geralmente necessário incluir o código usado para `x:Code` dentro de um `CDATA` segmento.  
  
 `x:Code` não é permitido em todos os mecanismos possíveis de implantação de produção XAML. O código deve ser compilado em estruturas específicas (por exemplo, WPF). Em outras estruturas, `x:Code` uso pode ser geralmente não permitido.  
  
 Estruturas que permitem gerenciado `x:Code` de conteúdo, o compilador de idioma correto a ser usado para `x:Code` conteúdo é determinado pelas configurações e destinos do projeto que é usado para compilar o aplicativo.  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 Código declarado em `x:Code` para WPF tem várias limitações importantes:  
  
-   O `x:Code` elemento de diretiva deve ser um elemento filho imediato do elemento raiz da produção XAML.  
  
-   [Diretiva X:Class](../../../docs/framework/xaml-services/x-class-directive.md) deve ser fornecido no elemento root pai.  
  
-   O código colocado em `x:Code` será tratado pela compilação como dentro do escopo da classe parcial que já está sendo criado para a página XAML. Portanto, todo código que você definir deve ser membros ou variáveis de classe parcial.  
  
-   Não é possível definir classes adicionais, que não seja de aninhamento de uma classe dentro da classe parcial (aninhamento é permitido, mas não é comum porque classes aninhadas não podem ser referenciados em XAML). Namespaces CLR que não seja o namespace que é usado para a classe parcial existente não pode ser definido ou adicionado ao.  
  
-   Referências a entidades de código fora o namespace CLR de classe parcial devem ser totalmente qualificadas. Se membros que estão sendo declarados são substituições para membros de classe parcial, isso deve ser especificado com a palavra-chave override específico do idioma. Se membros declarados em `x:Code` escopo estão em conflito com os membros da classe parcial criada fora do XAML, de forma que o compilador informa que o conflito, o arquivo XAML não é possível compilar ou carregar.  
  
## <a name="see-also"></a>Consulte também  
 [Diretiva x:Class](../../../docs/framework/xaml-services/x-class-directive.md)  
 [Code-behind e XAML no WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [Visão geral de XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
