---
title: 'Mitigação: verificações de dois-pontos no caminho'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: e88643fea3bd507289436f41880a2de34117884f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457901"
---
# <a name="mitigation-path-colon-checks"></a>Mitigação: verificações de dois-pontos no caminho
Começando com os aplicativos direcionados ao .NET Framework 4.6.2, várias alterações foram feitas para dar suporte aos caminhos anteriormente sem suporte (em termos de comprimento e formato). Em particular, as verificações da sintaxe adequada do separador de unidade (os dois-pontos) foram corrigidas.  
  
## <a name="impact"></a>Impacto  
 Essas alterações bloqueiam alguns caminhos de URI aos quais esses os métodos <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> e <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> anteriormente davam suporte.  
  
## <a name="mitigation"></a>Redução  
 Para contornar o problema de um caminho aceitável anteriormente que não tem mais suporte pelos métodos <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> e <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>, é possível fazer o seguinte:  
  
- Remova manualmente o esquema de uma URL. Por exemplo, remova `file://` de uma URL.  
  
- Passe o URI para um construtor <xref:System.Uri> e recupere o valor da propriedade <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType>.  
  
- Recuse a normalização do novo caminho definindo a opção `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> como `true`.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Compatibilidade de aplicativos](application-compatibility.md)
