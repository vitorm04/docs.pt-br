---
title: Como My depende do tipo de projeto (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: 72b9799d1f5ba7efa37d5f8f2a633e6806a58607
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63808082"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>Como My depende do tipo de projeto (Visual Basic)
`My` expõe apenas os objetos exigidos por um tipo de projeto específico. Por exemplo, o `My.Forms` objeto está disponível em um aplicativo Windows Forms, mas não está disponível em um aplicativo de console. Este tópico descreve quais `My` objetos estão disponíveis em diferentes tipos de projeto.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>Meu Windows em aplicativos e Sites da Web  
 `My` expõe apenas os objetos que são úteis para o tipo de projeto atual; Suprime a objetos que não são aplicáveis. Por exemplo, a imagem a seguir mostra o `My` modelo de objeto em um projeto Windows Forms.  
  
 ![Diagrama que mostra o meu modelo de objeto em um aplicativo Windows Forms.](./media/how-my-depends-on-project-type/my-object-model-windows-forms.png)  
  
 Em um projeto de site da Web, `My` expõe objetos que são relevantes para um desenvolvedor da Web (como o `My.Request` e `My.Response` objetos) enquanto suprime objetos que não são relevantes (como o `My.Forms` objeto). A imagem a seguir mostra o `My` modelo de objeto em um projeto de site da Web:  
  
 ![Diagrama que mostra o meu modelo de objeto em um aplicativo Web.](./media/how-my-depends-on-project-type/my-object-model-web.png)  
  
## <a name="project-details"></a>Detalhes do projeto  
 A tabela a seguir mostra quais `My` objetos estão ativados por padrão, para oito tipos de projeto: Aplicativo do Windows, biblioteca de classes, aplicativo de console, Windows biblioteca de controles, Web biblioteca de controle, Windows service, vazio e site da Web.  
  
 Há três versões do `My.Application` object, duas versões dos `My.Computer` objeto e duas versões do `My.User` do objeto; detalhes sobre essas versões são fornecidos nas notas de rodapé após a tabela.  
  
|Meu objeto|Aplicativo do Windows|Biblioteca de Classes|Aplicativo do Console|Biblioteca de controle do Windows|Biblioteca de controle da Web|Serviço do Windows|Vazio|Site da Web|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**Sim** <sup>1</sup>|**Sim** <sup>2</sup>|**Sim** <sup>3</sup>|**Sim** <sup>2</sup>|Não|**Sim** <sup>3</sup>|Não|Não|  
|`My.Computer`|**Sim** <sup>4</sup>|**Sim** <sup>4</sup>|**Sim** <sup>4</sup>|**Sim** <sup>4</sup>|**Sim** <sup>5</sup>|**Sim** <sup>4</sup>|Não|**Sim** <sup>5</sup>|  
|`My.Forms`|**Sim**|Não|Não|**Sim**|Não|Não|Não|Não|  
|`My.Log`|Não|Não|Não|Não|Não|Não|Não|**Sim**|  
|`My.Request`|Não|Não|Não|Não|Não|Não|Não|**Sim**|  
|`My.Resources`|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|Não|Não|  
|`My.Response`|Não|Não|Não|Não|Não|Não|Não|**Sim**|  
|`My.Settings`|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|Não|Não|  
|`My.User`|**Sim** <sup>6</sup>|**Sim** <sup>6</sup>|**Sim** <sup>6</sup>|**Sim** <sup>6</sup>|**Sim** <sup>7</sup>|**Sim** <sup>6</sup>|Não|**Sim** <sup>7</sup>|  
|`My.WebServices`|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|**Sim**|Não|Não|  
  
 <sup>1</sup> versão do Windows Forms do `My.Application`. Deriva da versão do console (veja a Observação 3); Adiciona suporte para a interação com o windows do aplicativo e fornece o modelo de aplicativo do Visual Basic.  
  
 <sup>2</sup> versão da biblioteca de `My.Application`. Fornece a funcionalidade básica necessitada por um aplicativo: fornece membros para gravar no log de aplicativo e acessar informações do aplicativo.  
  
 <sup>3</sup> versão do console do `My.Application`. Deriva a versão da biblioteca (consulte a Observação 2), e adiciona membros adicionais para acessar argumentos de linha de comando do aplicativo e informações de implantação do ClickOnce.  
  
 <sup>4</sup> versão do Windows do `My.Computer`. Deriva da versão do servidor (consulte a Observação 5) e fornece acesso a objetos úteis em um computador cliente, como o teclado, a tela e o mouse.  
  
 <sup>5</sup> versão do servidor de `My.Computer`. Fornece informações básicas sobre o computador, como o nome, o acesso ao relógio e assim por diante.  
  
 <sup>6</sup> versão do Windows do `My.User`. Este objeto está associado com a identidade do thread atual.  
  
 <sup>7</sup> versão da web `My.User`. Este objeto está associado com a identidade do usuário da solicitação HTTP do aplicativo atual.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Personalizando quais objetos estão disponíveis em My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/Define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [Objeto My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
- [Objeto My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)
- [Objeto My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
