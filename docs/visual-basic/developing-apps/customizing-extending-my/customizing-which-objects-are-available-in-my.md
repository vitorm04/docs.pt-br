---
title: Personalizando quais objetos estão disponíveis em My (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: b06e71784a4d02bcbcd755d14e57ef88c4322f7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592134"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Personalizando quais objetos estão disponíveis em My (Visual Basic)
Este tópico descreve como você pode controlar quais `My` objetos são ativados pela configuração do seu projeto `_MYTYPE` constante de compilação condicional. O Visual Studio Integrated Development Environment (IDE) mantém o `_MYTYPE` constante de compilação condicional para um projeto em sincronia com o tipo do projeto.  
  
## <a name="predefined-mytype-values"></a>Valores predefinidos MYTYPE  
 Você deve usar o `/define` opção de compilador para definir o `_MYTYPE` constante de compilação condicional. Ao especificar seu próprio valor para o `_MYTYPE` constante, você deve colocar o valor de cadeia de caracteres de barra invertida/aspas (\\") sequências. Por exemplo, você pode usar:  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Esta tabela mostra que a `_MYTYPE` constante de compilação condicional está definida para vários tipos de projeto.  
  
|Tipo de projeto|Valor de MYTYPE|  
|------------------|--------------------|  
|Biblioteca de Classes|"Windows"|  
|Aplicativo do Console|"Console"|  
|Web|"Web"|  
|Biblioteca de controle da Web|"WebControl"|  
|Aplicativo do Windows|"WindowsForms"|  
|Aplicativo do Windows, ao iniciar com personalizado `Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Biblioteca de controle do Windows|"Windows"|  
|Serviço do Windows|"Console"|  
|Vazio|"Empty"|  
  
> [!NOTE]
>  Todas as comparações de cadeia de caracteres de compilação condicional diferenciam maiusculas de minúsculas, independentemente de como o `Option Compare` instrução é definida.  
  
## <a name="dependent-my-compilation-constants"></a>Constantes de compilação dependentes do My  
 O `_MYTYPE` constante de compilação condicional, por sua vez, controla os valores de várias outras `_MY` constantes de compilação:  
  
|_MYTYPE|MYAPPLICATIONTYPE|_MYCOMPUTERTYPE|_MYFORMS|_MYUSERTYPE|_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|"Console"|"Console"|"Windows"|Indefinido|"Windows"|TRUE|  
|"Custom"|Indefinido|Indefinido|Indefinido|Indefinido|Indefinido|  
|"Empty"|Indefinido|Indefinido|Indefinido|Indefinido|Indefinido|  
|"Web"|Indefinido|"Web"|FALSE|"Web"|FALSE|  
|"WebControl"|Indefinido|"Web"|FALSE|"Web"|TRUE|  
|"Windows" ou ""|"Windows"|"Windows"|Indefinido|"Windows"|TRUE|  
|"WindowsForms"|"WindowsForms"|"Windows"|TRUE|"Windows"|TRUE|  
|"WindowsFormsWithCustomSubMain"|"Console"|"Windows"|TRUE|"Windows"|TRUE|  
  
 Por padrão, as constantes de compilação condicional indefinidas resolver para `FALSE`. Você pode especificar valores para as constantes indefinidas ao compilar seu projeto para substituir o comportamento padrão.  
  
> [!NOTE]
>  Quando `_MYTYPE` é definido como "Custom", o projeto contém o `My` namespace, mas ele não contém objetos. Entretanto, a configuração `_MYTYPE` para "Empty" impede que o compilador adicione o `My` namespace e seus objetos.  
  
 Esta tabela descreve os efeitos dos valores predefinidos do `_MY` constantes de compilação.  
  
|Constante|Significado|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Permite `My.Application`, se a constante é "Console" Windows "ou"WindowsForms":<br /><br /> -A versão "Console" deriva de <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>. e tem menos membros do que a versão "Windows".<br />-A versão "Windows" é derivada de <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>e tem menos membros do que a versão "WindowsForms".<br />-A versão "WindowsForms" de `My.Application` deriva de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Se o `TARGET` constante é definida como "winexe", em seguida, a classe inclui um `Sub Main` método.|  
|`_MYCOMPUTERTYPE`|Permite `My.Computer`, se a constante é "Web" ou "Windows":<br /><br /> -A versão "Web" é derivada de <xref:Microsoft.VisualBasic.Devices.ServerComputer>, e tem menos membros do que a versão "Windows".<br />-A versão "Windows" do `My.Computer` deriva de <xref:Microsoft.VisualBasic.Devices.Computer>.|  
|`_MYFORMS`|Permite `My.Forms`, se a constante é `TRUE`.|  
|`_MYUSERTYPE`|Permite `My.User`, se a constante é "Web" ou "Windows":<br /><br /> -A versão "Web" de `My.User` está associado com a identidade do usuário da solicitação HTTP atual.<br />-A versão "Windows" do `My.User` está associado à entidade de segurança do thread atual.|  
|`_MYWEBSERVICES`|Permite `My.WebServices`, se a constante é `TRUE`.|  
|`_MYTYPE`|Permite `My.Log`, `My.Request`, e `My.Response`, se a constante é "Web".|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.Logging.Log>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [Como My depende do tipo de projeto](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)  
 [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [/Define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [Objeto My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)  
 [Objeto My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)  
 [Objeto My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
