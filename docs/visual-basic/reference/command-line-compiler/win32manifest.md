---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79b51117197f28cec21671eea4dd7b7f2f1cc306
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-win32manifest-visual-basic"></a>-win32manifest (Visual Basic)
Identifica um definido pelo usuário aplicativo arquivo manifesto Win32 a ser inserido no arquivo de PE (executável portátil) do projeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`fileName`|O caminho do arquivo de manifesto personalizado.|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, o compilador do Visual Basic incorpora um manifesto de aplicativo que especifica um nível de execução solicitado de asInvoker. Cria o manifesto na mesma pasta em que o arquivo executável é criado, normalmente a pasta bin\Debug ou bin\Release quando você usa o Visual Studio. Se você quiser fornecer um manifesto personalizado, por exemplo, para especificar um nível de execução solicitado de highestAvailable ou requireAdministrator, use essa opção para especificar o nome do arquivo.  
  
> [!NOTE]
>  Essa opção e o [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) opção são mutuamente exclusivos. Se você tentar usar ambas as opções na mesma linha de comando, você obterá um erro de compilação.  
  
 Um aplicativo que não tem nenhum manifesto do aplicativo que especifica que um nível de execução solicitado estará sujeito à virtualização de arquivos/Registro sob o recurso de Controle de Conta de Usuário no Windows Vista. Para obter mais informações sobre a virtualização, consulte [a implantação do ClickOnce no Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).  
  
 Seu aplicativo estará sujeito a virtualização se alguma das seguintes condições for verdadeira:  
  
1.  Você usa o `-nowin32manifest` opção e você não fornecer um manifesto em uma etapa de compilação posterior ou como parte de um arquivo de recurso do Windows (. res), usando o `-win32resource` opção.  
  
2.  Você fornece um manifesto personalizado que não especifica um nível de execução solicitado.  
  
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] cria um arquivo .manifest padrão e o armazena nos diretórios de depuração e liberação juntamente com o arquivo executável. Você pode exibir ou editar o arquivo App. manifest padrão clicando **exibir configurações de UAC** no **aplicativo** guia no Designer de projeto. Para obter mais informações, consulte [Página de aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 Você pode fornecer o manifesto do aplicativo como uma etapa de pós-compilação personalizada, ou como parte de um arquivo de recurso Win32 usando o `-nowin32manifest` opção. Use essa mesma opção se quiser que o aplicativo seja sujeito à virtualização de arquivo ou Registro no Windows Vista. Isso impedirá que o compilador de criar e inserir um manifesto padrão no arquivo PE.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o manifesto padrão que o compilador do Visual Basic insere em um PE.  
  
> [!NOTE]
>  O compilador insere um nome padrão de aplicativo MyApplication no manifesto XML. Essa é uma solução alternativa para habilitar os aplicativos para serem executados no Windows Server 2003 Service Pack 3.  
  
```xml  
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
 [-nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
