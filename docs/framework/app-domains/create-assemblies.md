---
title: Criando assemblies
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8490351b4ab1bb115e4bd7277f43ad22b144a2df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752059"
---
# <a name="creating-assemblies"></a>Criando assemblies
Você pode criar assemblies de vários arquivos ou um único arquivo usando um IDE, como [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] ou outros compiladores e ferramentas fornecidas pelo [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]. O assembly mais simples é um único arquivo que tem um nome simples e é carregado em um único domínio de aplicativo. Esse assembly não pode ser referenciado por outros assemblies fora do diretório do aplicativo e não é submetido à verificação de versão. Para desinstalar o aplicativo composto do assembly, você simplesmente exclui o diretório em que ele reside. Para muitos desenvolvedores, um assembly com esses recursos é tudo o que é necessário para implantar um aplicativo.  
  
 Você pode criar um assembly de vários arquivos de vários módulos de código e arquivos de recurso. Você também pode criar um assembly que pode ser compartilhado por vários aplicativos. Um assembly compartilhado deve ter um nome forte e pode ser implantado no cache de assembly global.  
  
 Você tem várias opções ao agrupar módulos de código e recursos em assemblies, dependendo dos seguintes fatores:  
  
-   Controle de versão  
  
     Agrupe módulos que devem ter as mesmas informações de versão.  
  
-   Implantação  
  
     Agrupe recursos e módulos de código que dão suporte ao seu modelo de implantação.  
  
-   Reutilização  
  
     Agrupe os módulos se eles puderem ser usados em conjunto de forma lógica para alguma finalidade. Por exemplo, um assembly composto pelos tipos e classes usados com pouca frequência para a manutenção do programa podem ser colocados no mesmo assembly. Além disso, os tipos que você pretende compartilhar com vários aplicativos devem ser agrupados em um assembly e o assembly deve ser assinado com um nome forte.  
  
-   Segurança  
  
     Agrupe módulos que contêm tipos que exigem as mesmas permissões de segurança.  
  
-   Definição de escopo  
  
     Agrupe módulos que contêm tipos cuja visibilidade deve ser restrita ao mesmo assembly.  
  
 Devem ser feitas considerações especiais ao disponibilizar assemblies de Common Language Runtime para aplicativos COM não gerenciados. Para obter mais informações sobre como trabalhar com código não gerenciado, consulte [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md) (Expondo componentes do .NET Framework para COM).  
  
## <a name="see-also"></a>Consulte também  
 [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Controle de versão do assembly](../../../docs/framework/app-domains/assembly-versioning.md)  
 [Como compilar um assembly de arquivo único](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 [Como Compilar um Assembly de Vários Arquivos](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Assemblies de vários arquivos](../../../docs/framework/app-domains/multifile-assemblies.md)
