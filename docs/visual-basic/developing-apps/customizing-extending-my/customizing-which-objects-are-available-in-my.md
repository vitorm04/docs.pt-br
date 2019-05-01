---
title: Personalizando quais objetos estão disponíveis em My (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: c0b47521c6a62071466ae4193cd8553bdfb3dcde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014226"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Personalizando quais objetos estão disponíveis em My (Visual Basic)

Este tópico descreve como você pode controlar quais `My` objetos são ativados pela configuração do seu projeto `_MYTYPE` constante de compilação condicional. O Visual Studio Development IDE (ambiente integrado) mantém o `_MYTYPE` constante de compilação condicional para um projeto em sincronia com o tipo do projeto.  
  
## <a name="predefined-mytype-values"></a>Predefinidas \_MYTYPE valores  

Você deve usar o `/define` opção de compilador para definir o `_MYTYPE` constante de compilação condicional. Ao especificar seu próprio valor para o `_MYTYPE` constante, você deve colocar o valor de cadeia de caracteres na marca de barra invertida/aspas (\\") sequências. Por exemplo, você pode usar:  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Esta tabela mostra que o `_MYTYPE` constante de compilação condicional está definida para vários tipos de projeto.  
  
|Tipo de projeto|\_Valor MYTYPE|  
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
> Todas as comparações de cadeia de caracteres de compilação condicional diferenciam maiusculas de minúsculas, independentemente de como a `Option Compare` instrução é definida.  
  
## <a name="dependent-my-compilation-constants"></a>Dependentes \_meu constantes de compilação  

O `_MYTYPE` constante de compilação condicional, por sua vez, controla os valores de várias outras `_MY` constantes de compilação:  
  
|\_MYTYPE|\_MYAPPLICATIONTYPE|\_MYCOMPUTERTYPE|\_MYFORMS|\_MYUSERTYPE|\_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|"Console"|"Console"|"Windows"|Indefinido|"Windows"|TRUE|  
|"Custom"|Indefinido|Indefinido|Indefinido|Indefinido|Indefinido|  
|"Empty"|Indefinido|Indefinido|Indefinido|Indefinido|Indefinido|  
|"Web"|Indefinido|"Web"|FALSE|"Web"|FALSE|  
|"WebControl"|Indefinido|"Web"|FALSE|"Web"|TRUE|  
|"Windows" ou ""|"Windows"|"Windows"|Indefinido|"Windows"|TRUE|  
|"WindowsForms"|"WindowsForms"|"Windows"|TRUE|"Windows"|TRUE|  
|"WindowsFormsWithCustomSubMain"|"Console"|"Windows"|TRUE|"Windows"|TRUE|  
  
 Por padrão, as constantes de compilação condicional indefinidas resolvem para `FALSE`. Você pode especificar valores para as constantes indefinidos ao compilar seu projeto para substituir o comportamento padrão.  
  
> [!NOTE]
> Quando `_MYTYPE` é definido como "Custom", o projeto contém o `My` namespace, mas ele não contém objetos. No entanto, definindo `_MYTYPE` para "Empty" impede que o compilador adicione o `My` namespace e seus objetos.  
  
 Esta tabela descreve os efeitos dos valores predefinidos do `_MY` constantes de compilação.  
  
|Constante|Significado|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Habilita `My.Application`, se a constante é "Console", Windows, "ou"WindowsForms":<br /><br /> -A versão "Console" deriva de <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>. e tem menos membros que a versão "Windows".<br />-A versão "Windows" deriva <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>e tem menos participantes que a versão "WindowsForms".<br />-A versão "WindowsForms" de `My.Application` deriva <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Se o `TARGET` constante é definida como "winexe", em seguida, a classe inclui um `Sub Main` método.|  
|`_MYCOMPUTERTYPE`|Habilita `My.Computer`, se a constante é "Web" ou "Windows":<br /><br /> -A versão "Web" deriva de <xref:Microsoft.VisualBasic.Devices.ServerComputer>, e tem menos membros que a versão "Windows".<br />-A versão "Windows" do `My.Computer` deriva <xref:Microsoft.VisualBasic.Devices.Computer>.|  
|`_MYFORMS`|Habilita `My.Forms`, se a constante é `TRUE`.|  
|`_MYUSERTYPE`|Habilita `My.User`, se a constante é "Web" ou "Windows":<br /><br /> -A versão da "Web" `My.User` está associado com a identidade do usuário da solicitação HTTP atual.<br />-A versão "Windows" do `My.User` está associado à entidade de segurança do thread atual.|  
|`_MYWEBSERVICES`|Habilita `My.WebServices`, se a constante é `TRUE`.|  
|`_MYTYPE`|Habilita `My.Log`, `My.Request`, e `My.Response`, se a constante é "Web".|  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Como My depende do tipo de projeto](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [/Define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [Objeto My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
- [Objeto My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)
- [Objeto My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
