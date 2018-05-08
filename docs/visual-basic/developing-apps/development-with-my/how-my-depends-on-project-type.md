---
title: Como My depende do tipo de projeto (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: d196309bb2780db757515bd6ba1927c5821e2475
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>Como My depende do tipo de projeto (Visual Basic)
`My` expõe apenas os objetos exigidos por um tipo de projeto específico. Por exemplo, o `My.Forms` objeto está disponível em um aplicativo de formulários do Windows, mas não está disponível em um aplicativo de console. Este tópico descreve quais `My` objetos estão disponíveis em diferentes tipos de projeto.  
  
## <a name="my-in-windows-applications-and-web-sites"></a>O Windows em Sites e aplicativos Web  
 `My` expõe somente objetos que são úteis para o tipo de projeto atual; suprime objetos que não são aplicáveis. Por exemplo, a imagem a seguir mostra o `My` modelo de objeto em um projeto de formulários do Windows.  
  
 ![Forma do meu em um aplicativo Windows Forms](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 Em um projeto de site da Web, `My` expõe objetos que são relevantes para o desenvolvedor da Web (como o `My.Request` e `My.Response` objetos) enquanto suprime objetos que não são relevantes (como o `My.Forms` objeto). A imagem a seguir mostra o `My` modelo de objeto em um projeto de site da Web:  
  
 ![Forma do meu em um aplicativo Web](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## <a name="project-details"></a>Detalhes do projeto  
 A tabela a seguir mostra quais `My` objetos habilitados por padrão para oito tipos de projeto: aplicativo do Windows, biblioteca de classes, aplicativo de console, biblioteca de controle do Windows, biblioteca de controle da Web, serviço do Windows, vazio e site da Web.  
  
 Há três versões do `My.Application` objeto, duas versões do `My.Computer` objeto e duas versões do `My.User` objeto; os detalhes sobre essas versões são fornecidos nas notas de rodapé após a tabela.  
  
|Objeto My|Aplicativo do Windows|Biblioteca de Classes|Aplicativo do Console|Biblioteca de controle do Windows|Biblioteca de controle da Web|Serviço do Windows|Vazio|Site da Web|  
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
  
 <sup>1</sup> versão de Windows Forms de `My.Application`. Deriva da versão do console (veja a Observação 3); Adiciona suporte para interação com janelas do aplicativo e fornece o modelo de aplicativo do Visual Basic.  
  
 <sup>2</sup> versão da biblioteca de `My.Application`. Fornece a funcionalidade básica necessitada para um aplicativo: fornece membros para gravar no log de aplicativo e acessar informações do aplicativo.  
  
 <sup>3</sup> versão do console de `My.Application`. Deriva da versão da biblioteca (consulte a Observação 2), e adiciona membros adicionais para acessar argumentos de linha de comando do aplicativo e as informações de implantação do ClickOnce.  
  
 <sup>4</sup> versão do Windows `My.Computer`. Deriva da versão do servidor (consulte a Observação 5) e fornece acesso a objetos úteis em um computador cliente, como o teclado, tela e mouse.  
  
 <sup>5</sup> versão de servidor `My.Computer`. Fornece informações básicas sobre o computador, como o nome, o acesso ao relógio e assim por diante.  
  
 <sup>6</sup> versão do Windows `My.User`. Este objeto é associado com a identidade do segmento atual.  
  
 <sup>7</sup> versão da web do `My.User`. Este objeto é associado com a identidade do usuário da solicitação HTTP atual do aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.Logging.Log>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [Personalizando quais objetos estão disponíveis em My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [/Define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [Objeto My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)  
 [Objeto My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)  
 [Objeto My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
