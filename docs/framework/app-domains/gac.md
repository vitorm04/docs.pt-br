---
title: Cache de assemblies global
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
caps.latest.revision: 13
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bad9e339896b0d62dce75a4044b18f3ae6a69332
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="global-assembly-cache"></a>Cache de assemblies global
Cada computador onde o Common Language Runtime está instalado tem um cache de código da máquina chamado cache de assembly global. O cache de assembly global armazena assemblies projetados especificamente para serem compartilhados por vários aplicativos no computador.  
  
 Você deve compartilhar assemblies instalando-os no cache de assembly global somente quando precisar. Como diretriz geral, mantenha as dependências de um assembly privadas e localize os assemblies no diretório de aplicativo, a menos que o compartilhamento de um assembly seja explicitamente obrigatório. Além disso, não é necessário instalar assemblies no cache de assembly global a fim de torná-los acessíveis para interoperabilidade COM ou código não gerenciado.  
  
> [!NOTE]
>  Há situações em que você explicitamente não deseja instalar um assembly no cache de assembly global. Se colocar um dos assemblies que compõem um aplicativo no cache de assembly global, você não poderá mais replicar nem instalar o aplicativo usando o comando **xcopy** para copiar o diretório do aplicativo. Você também deve mover o assembly no cache de assembly global.  
  
 Há duas maneiras de implantar um assembly no cache de assembly global:  
  
-   Use um instalador projetado para funcionar com o cache de assembly global. Essa é a opção preferencial para instalar assemblies no cache de assembly global.  
  
-   Use uma ferramenta de desenvolvedor chamada [Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), fornecida pelo [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
    > [!NOTE]
    >  Em cenários de implantação, use o Windows Installer para instalar assemblies no cache de assembly global. Só use a ferramenta Global Assembly Cache em cenários de desenvolvimento, porque ela não fornece contagem de referência de assembly e outros recursos fornecidos durante o uso do Windows Installer.  
  
 A partir do .NET Framework 4, o local padrão do cache de assembly global é **%windir%\Microsoft.NET\assembly**. Em versões anteriores do .NET Framework, o local padrão era **%windir%\assembly**.  
  
 Os administradores geralmente protegem o diretório systemroot usando uma ACL (lista de controle de acesso) para controlar acesso de escrita e execução. Como o cache de assembly global é instalado em um subdiretório do diretório systemroot, ele herda a ACL desse diretório. É recomendável que apenas usuários com privilégios Administrador tenham permissão para excluir arquivos do cache de assembly global.  
  
 Assemblies implantados no cache de assembly global devem ter um nome forte. Quando um assembly é adicionado ao cache de assembly global, são executadas verificações de integridade em todos os arquivos que compõem o assembly. O cache executa essas verificações de integridade para garantir que um assembly não tenha sido adulterado, por exemplo, quando um arquivo é alterado, mas o manifesto não reflete a alteração.  
  
## <a name="see-also"></a>Consulte também  
 [Assemblies no Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)   
 [Como trabalhar com assemblies e o cache de assembly global](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)   
 [Assemblies de nomes fortes](../../../docs/framework/app-domains/strong-named-assemblies.md)

