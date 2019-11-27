---
title: Personalizando quais objetos estão disponíveis em My
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: 0387aca08e3a31b0a2045369919894d88caf5b76
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330320"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Personalizando quais objetos estão disponíveis em My (Visual Basic)

Este tópico descreve como você pode controlar quais `My` objetos são habilitados definindo a constante de compilação condicional `_MYTYPE` do seu projeto. O IDE (ambiente de desenvolvimento integrado) do Visual Studio mantém a constante `_MYTYPE` a compilação condicional de um projeto em sincronia com o tipo do projeto.  
  
## <a name="predefined-_mytype-values"></a>Valores predefinidos de \_com MyType  

Você deve usar a opção de compilador `/define` para definir a constante de compilação condicional `_MYTYPE`. Ao especificar seu próprio valor para a constante de `_MYTYPE`, você deve colocar o valor da cadeia de caracteres nas sequências de barra invertida/aspas (\\"). Por exemplo, você pode usar:  
  
```console  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 Esta tabela mostra o que a constante de compilação condicional `_MYTYPE` está definida para vários tipos de projeto.  
  
|Tipo de projeto|\_valor de com MyType|  
|------------------|--------------------|  
|Biblioteca de classes|Windows|  
|Aplicativo do Console|MMC|  
|Web|Site|  
|Biblioteca de controle da Web|WebControl|  
|Aplicativo do Windows|WindowsForms|  
|Aplicativo do Windows, ao iniciar com `Sub Main` personalizado|"WindowsFormsWithCustomSubMain"|  
|Biblioteca de controle do Windows|Windows|  
|Serviço do Windows|MMC|  
|Vazio|Esvaziá|  
  
> [!NOTE]
> Todas as comparações de cadeias de caracteres de compilação condicional diferenciam maiúsculas de minúsculas, independentemente de como a instrução de `Option Compare` está definida.  
  
## <a name="dependent-_my-compilation-constants"></a>Dependentes de \_minhas constantes de compilação  

O `_MYTYPE` constante de compilação condicional, por sua vez, controla os valores de várias outras constantes de compilação `_MY`:  
  
|\_com MyType|\_myapplicationtype|\_mycomputertype|\_MyForms|\_myusertype|\_myWebServices|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|MMC|MMC|Windows|Indefinido|Windows|TRUE|  
|Personalizar|Indefinido|Indefinido|Indefinido|Indefinido|Indefinido|  
|Esvaziá|Indefinido|Indefinido|Indefinido|Indefinido|Indefinido|  
|Site|Indefinido|Site|FALSE|Site|FALSE|  
|WebControl|Indefinido|Site|FALSE|Site|TRUE|  
|"Windows" ou ""|Windows|Windows|Indefinido|Windows|TRUE|  
|WindowsForms|WindowsForms|Windows|TRUE|Windows|TRUE|  
|"WindowsFormsWithCustomSubMain"|MMC|Windows|TRUE|Windows|TRUE|  
  
 Por padrão, as constantes de compilação condicional indefinidas são resolvidas para `FALSE`. Você pode especificar valores para as constantes indefinidas ao compilar seu projeto para substituir o comportamento padrão.  
  
> [!NOTE]
> Quando `_MYTYPE` é definido como "Custom", o projeto contém o namespace `My`, mas não contém nenhum objeto. No entanto, definir `_MYTYPE` como "Empty" impede que o compilador adicione o namespace `My` e seus objetos.  
  
 Esta tabela descreve os efeitos dos valores predefinidos das constantes de compilação `_MY`.  
  
|Constante|Significado|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Habilita `My.Application`, se a constante for "console", Windows, "ou" WindowsForms ":<br /><br /> -A versão do "console" deriva de <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>. e tem menos membros do que a versão "Windows".<br />-A versão "Windows" deriva de <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>. e tem menos membros do que a versão "WindowsForms".<br />-A versão "WindowsForms" do `My.Application` deriva de <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Se a constante de `TARGET` for definida como "winexe", a classe incluirá um método `Sub Main`.|  
|`_MYCOMPUTERTYPE`|Habilita `My.Computer`, se a constante for "Web" ou "Windows":<br /><br /> -A versão "Web" deriva de <xref:Microsoft.VisualBasic.Devices.ServerComputer>e tem menos membros do que a versão "Windows".<br />-A versão do "Windows" do `My.Computer` deriva de <xref:Microsoft.VisualBasic.Devices.Computer>.|  
|`_MYFORMS`|Habilita `My.Forms`, se a constante for `TRUE`.|  
|`_MYUSERTYPE`|Habilita `My.User`, se a constante for "Web" ou "Windows":<br /><br /> -A versão "Web" do `My.User` está associada à identidade do usuário da solicitação HTTP atual.<br />-A versão "Windows" do `My.User` está associada à entidade de segurança atual do thread.|  
|`_MYWEBSERVICES`|Habilita `My.WebServices`, se a constante for `TRUE`.|  
|`_MYTYPE`|Habilita `My.Log`, `My.Request`e `My.Response`, se a constante for "Web".|  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.Logging.Log>
- <xref:Microsoft.VisualBasic.ApplicationServices.User>
- [Como My depende do tipo de projeto](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)
- [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [-definir (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [Objeto My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)
- [Objeto My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)
- [Objeto My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)
- [Objeto My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
