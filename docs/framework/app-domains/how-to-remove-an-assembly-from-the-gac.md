---
title: Como remover um assembly do cache de assemblies global
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f3f5d6ae577195987dfcf2d8020e591217b480d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502991"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a>Como remover um assembly do cache de assemblies global
Há duas maneiras de remover um assembly do GAC (cache de assemblies global):  
  
-   Usando a [Ferramenta Cache de Assembly Global (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md). Use essa opção para desinstalar assemblies que você colocou no GAC durante o desenvolvimento e teste.  
  
-   Usando o [Windows Installer](/windows/desktop/Msi/windows-installer-portal). Use essa opção para desinstalar assemblies ao testar pacotes de instalação e para sistemas de produção.  
  
### <a name="removing-an-assembly-with-gacutilexe"></a>Remover um assembly com o Gacutil.exe  
  
1.  No prompt de comando, digite o seguinte comando:  
  
     **gacutil –u** \<*nome do assembly*>  
  
     Neste comando, *nome do assembly* é o nome do assembly a ser removido do cache de assembly global.  
  
    > [!WARNING]
    >  Não use Gacutil.exe para remover assemblies em sistemas de produção devido à possibilidade de que o assembly ainda possa ser necessário para algum aplicativo. Em vez disso, use o Windows Installer, que mantém uma contagem de referência para cada assembly que ele instala no GAC.  
  
 O exemplo a seguir remove um assembly chamado `hello.dll` do cache de assembly global.  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a>Remover um assembly com o Windows Installer  
  
1.  No aplicativo **Programas e Recursos**, em **Painel de Controle**, selecione o aplicativo que você deseja desinstalar. Se o pacote de instalação tiver colocado assemblies no GAC, o Windows Installer os removerá se não forem usados por outro aplicativo.  
  
    > [!NOTE]
    >  O Windows Installer mantém uma contagem de referência para os assemblies instalados no GAC. Um assembly será removido do GAC apenas quando sua contagem de referência atingir zero, o que indica que ele não é usado por qualquer aplicativo instalado por um pacote do Windows Installer.  
  
## <a name="see-also"></a>Consulte também  
 [Como trabalhar com assemblies e o cache de assembly global](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Como instalar um assembly no cache de assembly global](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [Gacutil.exe (Ferramenta do Cache de Assemblies Global)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
