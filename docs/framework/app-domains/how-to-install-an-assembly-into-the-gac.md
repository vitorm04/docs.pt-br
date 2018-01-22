---
title: Como instalar um assembly no cache de assemblies global
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98dd4d1e75fc37820a1b1f4eccfa48f978772687
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Como instalar um assembly no cache de assemblies global
Há duas maneiras de instalar um assembly com nome forte no GAC (Cache de Assembly Global):  
  
> [!IMPORTANT]
>  Apenas os assemblies com nome forte podem ser instalados no GAC. Para obter informações sobre como criar um assembly de nome forte, consulte [Como assinar um assembly com um nome forte](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
-   Usando o [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).  
  
     Você faz isso no Visual Studio 2012 e no Visual Studio 2013 ao criar um projeto do InstallShield Limited Edition.  
  
     Essa é a maneira recomendada e mais comum de adicionar assemblies no Cache de Assembly Global. O instalador fornece uma contagem de referência de assemblies no Cache de Assembly Global, além de outros benefícios.  
  
-   Usando a [Ferramenta Cache de Assembly Global (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
     Você pode usar o Gacutil.exe para adicionar assemblies com nome forte ao Cache de Assembly Global e para exibir o conteúdo desse cache.  
  
    > [!NOTE]
    >  Gacutil.exe destina-se a fins de desenvolvimento e não deve ser usado para instalar assemblies de produção no Cache de Assembly Global.  
  
> [!NOTE]
>  Nas versões anteriores do .NET Framework, a extensão do shell do Windows Shfusion.dll permitia instalar assemblies arrastando-os no Explorador de Arquivos. A partir do [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], o Shfusion.dll tornou-se obsoleto.  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a>Para usar a ferramenta Cache de Assembly Global (Gacutil.exe)  
  
1.  No prompt de comando, digite o seguinte comando:  
  
     **gacutil -i** \<*nome do assembly*>  
  
     Neste comando, *nome do assembly* é o nome do assembly a ser instalado no cache de assembly global.  
  
 O exemplo a seguir instala um assembly com nome de arquivo `hello.dll` no Cache de Assembly Global.  
  
```  
gacutil -i hello.dll  
```  
  
 Para obter mais informações, consulte [Ferramenta Cache de Assembly Global (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).  
  
### <a name="to-use-an-installshield-limited-edition-project"></a>Para usar um projeto do InstallShield Limited Edition  
  
1.  Adicione um pacote de instalação e implantação à sua solução ao abrir o menu de atalho para a solução e, em seguida, escolha **Adicionar**, **Novo Projeto**.  
  
2.  Na caixa de diálogo **Adicionar Novo Projeto**, na pasta **Instalado**, escolha **Outros Tipos de Projeto**, **Instalação e Implantação**, **InstallShield Limited Edition** e atribua um nome ao projeto. (Se solicitado, baixe, instale e ative o InstallShield.)  
  
3.  Faça a configuração geral do seu projeto de instalação e implantação usando o Assistente de Projeto no **Gerenciador de Soluções** ou escolhendo as subetapas das etapas numeradas no **Gerenciador de Soluções**. Configure sua instalação como faria se não estivesse adicionando assemblies ao GAC.  
  
4.  Para iniciar o processo de adicionar um assembly ao GAC, escolha **Arquivos**, sob a etapa **Especificar Dados do Aplicativo** no **Gerenciador de Soluções**.  
  
5.  No painel **Pastas do computador de destino**, abra o menu de atalho para **Computador de Destino** e escolha **Mostrar Pasta Predefinida**, **[GlobalAssemblyCache]**.  
  
6.  Para cada projeto na solução que contém um assembly que você deseja instalar no Cache de assembly Global:  
  
    1.  No painel **Pastas do computador de origem**, escolha o projeto.  
  
    2.  No painel **Pastas do computador de destino**, escolha **[GlobalAssemblyCache]**.  
  
    3.  No painel **Arquivos do computador de origem**, escolha **Saída primária de** *<project_name>*.  
  
    4.  Arraste o arquivo na etapa c para o painel **Arquivos do computador de destino** (ou use os comandos **Copiar** e **Colar** no menu de atalho de arquivo).  
  
## <a name="see-also"></a>Consulte também  
 [Como trabalhar com assemblies e o cache de assembly global](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Como remover um assembly do cache de assembly global](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [Gacutil.exe (Ferramenta do Cache de Assemblies Global)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [Como assinar um assembly com um nome forte](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [implantação do Windows Installer](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
