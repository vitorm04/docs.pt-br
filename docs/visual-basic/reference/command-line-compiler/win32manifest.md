---
title: /win32manifest (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: b07d5816e5bb80a95e608fa7214a2db48ebac0dc
ms.lasthandoff: 03/13/2017

---
# <a name="win32manifest-visual-basic"></a>/win32manifest (Visual Basic)
Identifica um definido pelo usuário aplicativo arquivo de manifesto Win32 a ser inserido no arquivo PE (portable executable) de um projeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/win32manifest: fileName  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`fileName`|O caminho do arquivo de manifesto personalizado.|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, o compilador Visual Basic insere um manifesto de aplicativo que especifica um nível de execução solicitado de asInvoker. Cria o manifesto na mesma pasta em que o arquivo executável é criado, normalmente a pasta bin\Debug ou bin\Release quando você usa o Visual Studio. Se você quiser fornecer um manifesto personalizado, por exemplo, para especificar um nível de execução solicitado de highestAvailable ou requireAdministrator, use essa opção para especificar o nome do arquivo.  
  
> [!NOTE]
>  Essa opção e o [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) opção são mutuamente exclusivos. Se você tentar usar ambas as opções na mesma linha de comando, você obterá um erro de compilação.  
  
 Um aplicativo que não tenha nenhum aplicativo de manifesto que especifica que um nível de execução solicitado estará sujeita a virtualização de arquivo/registro sob o recurso de controle de conta de usuário no Windows Vista. Para obter mais informações sobre virtualização, consulte [implantação do ClickOnce no Windows Vista](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista).  
  
 Seu aplicativo estará sujeito a virtualização se alguma das seguintes condições for verdadeira:  
  
1.  Você usa o `/nowin32manifest` opção e você não fornecer um manifesto em uma etapa posterior da compilação ou como parte de um arquivo Windows Resource (. res), usando o `/win32resource` opção.  
  
2.  Fornecer um manifesto personalizado que não especifica um nível de execução solicitado.  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]cria um arquivo padrão de manifesto e o armazena nos diretórios de depuração e versão junto do arquivo executável. Você pode exibir ou editar o arquivo padrão App clicando **exibir configurações de UAC** sobre o **aplicativo** guia no Designer de projeto. Para obter mais informações, consulte [página de aplicativo, Designer de projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 Você pode fornecer o manifesto do aplicativo como uma etapa de pós-compilação personalizada ou como parte de um arquivo de recurso Win32 usando o `/nowin32manifest` opção. Use essa mesma opção se quiser que o aplicativo seja sujeito à virtualização de arquivo ou registro no Windows Vista. Isso impedirá que o compilador crie e incorpore um manifesto padrão no arquivo PE.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o manifesto padrão que o compilador Visual Basic insere em um PE.  
  
> [!NOTE]
>  O compilador insere um nome padrão de aplicativo MyApplication no manifesto XML. Essa é uma solução para habilitar aplicativos executados no Windows Server 2003 Service Pack 3.  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
