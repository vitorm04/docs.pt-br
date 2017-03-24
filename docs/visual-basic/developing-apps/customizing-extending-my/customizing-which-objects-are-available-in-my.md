---
title: "Personalizando quais objetos estão disponíveis em My (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My namespace, customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6791398270e4348adf356eb36a385bfbefde873c
ms.lasthandoff: 03/13/2017

---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Personalizando quais objetos estão disponíveis em My (Visual Basic)
Este tópico descreve como você pode controlar quais `My` objetos são ativados pela configuração do seu projeto `_MYTYPE` constante de compilação condicional. O [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) mantém o `_MYTYPE` constante de compilação condicional para um projeto em sincronia com o tipo do projeto.  
  
## <a name="predefined-mytype-values"></a>Valores predefinidos MYTYPE  
 Você deve usar o `/define` opção de compilador para definir o `_MYTYPE` constante de compilação condicional. Ao especificar seu próprio valor para a `_MYTYPE` constante, você deve colocar o valor de cadeia de caracteres de barra invertida/aspas (\\") sequências. Por exemplo, você pode usar:  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Esta tabela mostra que a `_MYTYPE` constante de compilação condicional está definida para vários tipos de projeto.  
  
|Tipo de projeto|Valor de MYTYPE|  
|------------------|--------------------|  
|Biblioteca de Classes|"Windows"|  
|Aplicativo do Console|"Console"|  
|Web|"Web"|  
|Biblioteca de Controles da Web|"WebControl"|  
|Aplicativo do Windows|"WindowsForms"|  
|Aplicativo do Windows, quando inicia com personalizado`Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Biblioteca de controle do Windows|"Windows"|  
|Serviço do Windows|"Console"|  
|Vazio|"Vazio"|  
  
> [!NOTE]
>  Todas as comparações de cadeia de caracteres de compilação condicional diferenciam maiusculas de minúsculas, independentemente de como a `Option Compare` instrução é definida.  
  
## <a name="dependent-my-compilation-constants"></a>Constantes de compilação dependentes do My  
 O `_MYTYPE` constante de compilação condicional, por sua vez, controla os valores de várias outras `_MY` constantes de compilação:  
  
|_MYTYPE|_MYAPPLICATIONTYPE|_MYCOMPUTERTYPE|_MYFORMS|_MYUSERTYPE|_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|"Console"|"Console"|"Windows"|Indefinido|"Windows"|TRUE|  
|"Custom"|Indefinido|Indefinido|Indefinido|Indefinido|Indefinido|  
|"Vazio"|Indefinido|Indefinido|Indefinido|Indefinido|Indefinido|  
|"Web"|Indefinido|"Web"|FALSE|"Web"|FALSE|  
|"WebControl"|Indefinido|"Web"|FALSE|"Web"|TRUE|  
|"Windows" ou ""|"Windows"|"Windows"|Indefinido|"Windows"|TRUE|  
|"WindowsForms"|"WindowsForms"|"Windows"|TRUE|"Windows"|TRUE|  
|"WindowsFormsWithCustomSubMain"|"Console"|"Windows"|TRUE|"Windows"|TRUE|  
  
 Por padrão, constantes de compilação condicional indefinidas são consideradas resolvem para `FALSE`. Você pode especificar valores para as constantes indefinidas ao compilar seu projeto para substituir o comportamento padrão.  
  
> [!NOTE]
>  Quando `_MYTYPE` é definido como "Custom", o projeto contém o `My` namespace, mas ele não contém objetos. No entanto, definir `_MYTYPE` para "Empty" impede que o compilador adicione o `My` namespace e seus objetos.  
  
 Esta tabela descreve os efeitos dos valores predefinidos do `_MY` constantes de compilação.  
  
|Constante|Significado|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Permite `My.Application`, se a constante é "Console" Windows "ou"WindowsForms":<br /><br /> -A versão "Console" é derivada de <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>.</xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> e tem menos participantes que a versão "Windows".<br />-A versão "Windows" é derivada de <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>e tem menos participantes que a versão "WindowsForms".</xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase><br />-A versão "WindowsForms" de `My.Application` deriva de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> Se o `TARGET` constante é definida como "winexe", então a classe inclui um `Sub Main` método.|  
|`_MYCOMPUTERTYPE`|Permite `My.Computer`, se a constante é "Web" ou "Windows":<br /><br /> -A versão "Web" é derivada de <xref:Microsoft.VisualBasic.Devices.ServerComputer>, e tem menos participantes que a versão "Windows".</xref:Microsoft.VisualBasic.Devices.ServerComputer><br />-A versão "Windows" do `My.Computer` deriva de <xref:Microsoft.VisualBasic.Devices.Computer>.</xref:Microsoft.VisualBasic.Devices.Computer>|  
|`_MYFORMS`|Permite `My.Forms`, se a constante é `TRUE`.|  
|`_MYUSERTYPE`|Permite `My.User`, se a constante é "Web" ou "Windows":<br /><br /> -A versão "Web" do `My.User` está associado com a identidade do usuário da solicitação HTTP atual.<br />-A versão "Windows" do `My.User` está associado com a principal da thread atual.|  
|`_MYWEBSERVICES`|Permite `My.WebServices`, se a constante é `TRUE`.|  
|`_MYTYPE`|Permite `My.Log`, `My.Request`, e `My.Response`, se a constante é "Web".|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer></xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.Logging.Log></xref:Microsoft.VisualBasic.Logging.Log>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User></xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [Como My depende do tipo de projeto](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)   
 [Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [/Define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)   
 [Objeto My. Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [Objeto My. Request](../../../visual-basic/language-reference/objects/my-request-object.md)   
 [Objeto My. Response](../../../visual-basic/language-reference/objects/my-response-object.md)   
 [Objeto My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
