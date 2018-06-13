---
title: Ferramentas do .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- command line, .NET Framework tools
- .NET Framework, tools
- tools [.NET Framework]
- running .NET Framework tools
ms.assetid: a2ca532d-91f7-426a-9303-417c2ee1247c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8ec8a5b1f665196fee62a4556e59201f45a6bff
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2018
ms.locfileid: "34312034"
---
# <a name="net-framework-tools"></a>Ferramentas do .NET Framework
A ferramentas do .NET Framework facilitam a criação, a implantação e o gerenciamento de aplicativos e componentes com o .NET Framework como destino.  
  
A maioria das ferramentas do .NET Framework descritas nesta seção é instalada automaticamente com o Visual Studio. Para baixar o Visual Studio, visite a página [Downloads do Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).
  
 É possível executar todas as ferramentas na linha de comando, com a exceção do Assembly Cache Viewer (Shfusion.dll). Você deve acessar Shfusion.dll no Explorador de Arquivos.  
  
 A melhor maneira de executar as ferramentas de linha de comando é usando o Prompt de Comando do Desenvolvedor do Visual Studio. Esses utilitários permitem executar facilmente as ferramentas, sem navegar até a pasta de instalação. Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
>  Algumas ferramentas são específicas para computadores 32 ou 64 bits. Não se esqueça de executar a versão apropriada da ferramenta para o computador.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Al.exe (Assembly Linker)](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 Gera um arquivo que tem um manifesto de assembly com base em módulos ou arquivos de recurso.  
  
 [Aximp.exe (Importador de Controle ActiveX do Windows Forms)](../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)  
 Converte definições de tipo em uma biblioteca de tipos COM para um controle ActiveX em um controle do Windows Forms.  
  
 [Caspol.exe (Ferramenta de Política de Segurança de Acesso do Código)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)  
 Permite exibir e configurar a política de segurança para o nível de política do computador, o nível de política do usuário e o nível de política da empresa. No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] e posteriores, essa ferramenta não afeta a política de CAS (segurança de acesso do código), a menos que o elemento [\<legacyCasPolicy>](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) seja definido como `true`. Para saber mais, confira [Alterações de segurança](../../../docs/framework/security/security-changes.md).  
  
 [Cert2spc.exe (Ferramenta de Teste de Certificado do Fornecedor de Software)](../../../docs/framework/tools/cert2spc-exe-software-publisher-certificate-test-tool.md)  
 Cria um SPC (Software Publisher's Certificate) de um ou mais certificados X.509. Essa ferramenta destina-se apenas a testes.  
  
 [Certmgr.exe (Ferramenta Gerenciador de Certificados)](../../../docs/framework/tools/certmgr-exe-certificate-manager-tool.md)  
 Gerencia certificados, CTLs (listas de certificados confiáveis) e CRLs (listas de certificados revogados).  
  
 [Clrver.exe (Ferramenta de Versão do CLR)](../../../docs/framework/tools/clrver-exe-clr-version-tool.md)  
 Relata todas as versões instaladas do CLR (Common Language Runtime) no computador.  
  
 [CorFlags.exe (Ferramenta de Conversão CorFlags)](../../../docs/framework/tools/corflags-exe-corflags-conversion-tool.md)  
 Permite configurar a seção CorFlags do cabeçalho de uma imagem PE.  
  
 [Fuslogvw.exe (Visualizador de Log de Associação de Assembly)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md)  
 Exibe informações sobre associações de assembly para ajudar a diagnosticar por que o .NET Framework não pode localizar um assembly no tempo de execução.  
  
 [Gacutil.exe (Ferramenta do Cache de Assemblies Global)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 Permite exibir e manipular o conteúdo do cache de assembly global e o cache de download.  
  
 [Ilasm.exe (IL Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md)  
 Gera um arquivo PE com base em IL. É possível executar o executável resultante para determinar se o IL é realizado conforme esperado.  
  
 [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)  
 Utiliza um arquivo PE que contém o código IL e cria um arquivo de texto que pode ser inserido no IL Assembler (Ilasm.exe).  
  
 [Installutil.exe (Ferramenta de Instalação)](../../../docs/framework/tools/installutil-exe-installer-tool.md)  
 Permite instalar e desinstalar recursos de servidor executando os componentes de instalador em um assembly especificado. (Funciona com classes no namespace <xref:System.Configuration.Install>.) Permite instalar e desinstalar recursos de servidor executando os componentes de instalador em um assembly especificado. (Funciona com classes no namespace <xref:System.Configuration.Install>.)  
  
 [Lc.exe (Compilador de Licença)](../../../docs/framework/tools/lc-exe-license-compiler.md)  
 Lê arquivos de texto que contêm informações de licenciamento e produz um arquivo .licenses que pode ser inserido em um executável do Common Language Runtime como um recurso. Lê arquivos de texto que contêm informações de licenciamento e produz um arquivo .licenses que pode ser inserido em um executável do Common Language Runtime como um recurso.  
  
 [Mage.exe (Manifest Generation and Editing Tool)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 Permite criar, editar e assinar manifestos de aplicativo e implantação. Como uma ferramenta de linha de comando, Mage.exe pode ser executado com base tanto em scripts de lote quanto em aplicativos com base no Windows, inclusive aplicativos do ASP.NET.  
  
 [MageUI.exe (Manifest Generation and Editing Tool, cliente gráfico)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
 Dá suporte à mesma funcionalidade que a ferramenta de linha de comando Mage.exe, mas usa uma interface do usuário (UI) com base no Windows. Dá suporte à mesma funcionalidade que a ferramenta de linha de comando Mage.exe, mas usa uma interface do usuário (UI) com base no Windows.  
  
 [MDbg.exe (Depurador de Linha de Comando do .NET Framework)](../../../docs/framework/tools/mdbg-exe.md)  
 Ajuda fornecedores de ferramentas e desenvolvedores de aplicativos na localização e na correção de bugs em programas com o Common Language Runtime do .NET Framework como destino. Essa ferramenta usa a API de depuração do tempo de execução para fornecer serviços de depuração.  
  
 [Mgmtclassgen.exe (Gerador de Classe Fortemente Tipada de Gerenciamento)](../../../docs/framework/tools/mgmtclassgen-exe.md)  
 Permite gerar uma classe gerenciada Early Bound para uma classe WMI (Windows Management Instrumentation) especificada.  
  
 [Mpgo.exe (Ferramenta de Otimização Guiada por Perfil Gerenciado)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md)  
 Permite ajustar assemblies de imagem nativa que usam cenários de usuário final comuns. Mpgo.exe permite a geração e o consumo dos dados de perfil para assemblies de aplicativo de imagem nativa (não assemblies do .NET Framework) que usam os cenários de treinamento selecionados pelo desenvolvedor de aplicativos.  
  
 [Ngen.exe (Gerador de Imagens Nativas)](../../../docs/framework/tools/ngen-exe-native-image-generator.md)  
 Melhora o desempenho de aplicativos gerenciados por meio do uso de imagens nativas (arquivos contendo o código do computador específico do processador compilado). O tempo de execução pode usar imagens nativas do cache em vez de usar o compilador JIT (Just-In-Time) para compilar o assembly original.  
  
 [Peverify.exe (Ferramenta PEVerify)](../../../docs/framework/tools/peverify-exe-peverify-tool.md)  
 Ajuda a verificar se o código MSIL (Microsoft intermediate language) e os metadados associados atendem aos requisitos de segurança de tipo. Ajuda a verificar se o código MSIL (Microsoft intermediate language) e os metadados associados atendem aos requisitos de segurança de tipo.  
  
 [Regasm.exe (Ferramenta de Registro de Assembly)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)  
 Lê os metadados dentro de um assembly e adiciona as entradas necessárias ao Registro. Isso permite que clientes COM sejam exibidos como classes do .NET Framework.  
  
 [Regsvcs.exe (Ferramenta de Instalação de Serviços .NET)](../../../docs/framework/tools/regsvcs-exe-net-services-installation-tool.md)  
 Carrega e registra um assembly, gera e instala uma biblioteca de tipos em um aplicativo COM+ versão 1.0 especificado, além de configurar serviços adicionados programaticamente a uma classe.  
  
 [Resgen.exe (Gerador de Arquivo de Recurso)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 Converte arquivos de texto (.txt ou .restext) e arquivos de recurso com base em XML (.resx) em arquivos binários do Common Language Runtime (.resources) que podem ser inseridos em um executável binário do tempo de execução ou compilados em assemblies satélite.  
  
 [SecAnnotate.exe (Ferramenta Anotador de Segurança do .NET)](../../../docs/framework/tools/secannotate-exe-net-security-annotator-tool.md)  
 Identifica as partes SecurityCritical e SecuritySafeCritical de um assembly. Identifica as partes `SecurityCritical` e `SecuritySafeCritical` de um assembly.  
  
 [SignTool.exe (Ferramenta de Assinatura)](../../../docs/framework/tools/signtool-exe.md)  
 Assina digitalmente arquivos, verifica assinaturas em arquivos e aplica carimbos de data/hora em arquivos.  
  
 [Sn.exe (Ferramenta Nome Forte)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 Ajuda a criar assemblies com nomes fortes. Esta ferramenta oferece opções para o gerenciamento de chaves, geração de assinaturas e verificação de assinaturas.  
  
 [SOS.dll (Extensão de Depuração SOS)](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md)  
 Ajuda a depurar programas gerenciados no depurador WinDbg.exe e no Visual Studio fornecendo informações sobre o ambiente interno do CLR (Common Language Runtime).  
  
 [SqlMetal.exe (Ferramenta de Geração de Código)](../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 Gera o código e o mapeamento para o componente LINQ to SQL do .NET Framework.  
  
 [Storeadm.exe (Ferramenta de Armazenamento Isolado)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md)  
 Gerencia o armazenamento isolado; dá opções para listar os repositórios do usuário e excluí-los.  
  
 [Tlbexp.exe (Exportador de Biblioteca de Tipos)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)  
 Gera uma biblioteca de tipos que descreve os tipos definidos em um assembly do Common Language Runtime.  
  
 [Tlbimp.exe (Importador de Biblioteca de Tipos)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 Converte as definições de tipo encontradas em uma biblioteca de tipos COM em definições equivalentes em um assembly do Common Language Runtime.  
  
 [Winmdexp.exe (Ferramenta de Exportação de Metadados do Tempo de Execução do Windows)](../../../docs/framework/tools/winmdexp-exe-windows-runtime-metadata-export-tool.md)  
 Exporta um assembly do .NET Framework que é compilado como um arquivo .winmdobj em um componente do Tempo de Execução do Windows, que é empacotado como um arquivo .winmd que contém informações de implementação e metadados do Tempo de Execução do Windows.  
  
 [Winres.exe (Editor de Recursos do Windows Forms)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)  
 Ajuda a localizar os recursos de interface do usuário (arquivos .resx ou .resources) usados pelo Windows Forms. É possível converter cadeias de caracteres e, em seguida, dimensionar, mover e ocultar controles para acomodar as cadeias de caracteres localizadas.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Ferramentas](http://msdn.microsoft.com/library/f533241c-317c-445e-88ca-c80c8d078fca)  
 Inclui ferramentas como a Conformidade do isXPS (isXPS.exe) e ferramentas de criação de perfil de desempenho.  
  
 [Ferramentas do Windows Communication Foundation](../../../docs/framework/wcf/tools.md)  
 Inclui ferramentas que facilitam a criação, a implantação e o gerenciamento de aplicativos do WCF (Windows Communication Foundation).
