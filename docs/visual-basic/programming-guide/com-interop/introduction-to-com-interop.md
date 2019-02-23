---
title: Introdução à interoperabilidade COM (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: e4421cbc40cdccc1dbbaeb459cb12fda0ee407cf
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745593"
---
# <a name="introduction-to-com-interop-visual-basic"></a>Introdução à interoperabilidade COM (Visual Basic)
O modelo de objeto de componente (COM) permite que um objeto exponha sua funcionalidade a outros componentes e aplicativos host. Embora os objetos COM tenham sido fundamentais para o Windows por muitos anos de programação, os aplicativos projetados para o common language runtime (CLR) oferecem várias vantagens.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplicativos eventualmente substituirão aqueles desenvolvidos com. Até lá, talvez você precise usar ou criar objetos COM usando o Visual Studio. Interoperabilidade com, ou *interoperabilidade*, permite que você use objetos COM existentes ao fazer a transição para o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] em seu próprio ritmo.  
  
 Usando o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] para criar componentes COM, você pode usar a interoperabilidade COM sem registro. Isso lhe permite controlar qual versão DLL é ativada quando mais de uma versão é instalada em um computador e permite que os usuários finais usar XCOPY ou FTP para copiar seu aplicativo para um diretório apropriado no computador onde ele pode ser executado. Para obter mais informações, consulte [interoperabilidade COM sem registro](../../../framework/interop/registration-free-com-interop.md).  
  
## <a name="managed-code-and-data"></a>O código gerenciado e dados  
 O código desenvolvido para o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] é chamado de *código gerenciado*e contém metadados que é usado pelo CLR. Dados usados pelo [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplicativos é chamado *dados gerenciados* porque o tempo de execução gerencia tarefas relacionadas a dados, como alocar e recuperar memória e executar verificação de tipo. Por padrão, o Visual Basic .NET usa código gerenciado e dados, mas você pode acessar o código não gerenciado e os dados de objetos COM usando assemblies de interoperabilidade (descritos posteriormente nesta página).  
  
## <a name="assemblies"></a>Assemblies  
 Um assembly é o principal bloco de construção de um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplicativo. É uma coleção de funcionalidade que é criado, com controle de versão e implantados como uma unidade única implementação que contém um ou mais arquivos. Cada assembly contém um manifesto do assembly.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Bibliotecas de tipos de manifestos de Assembly  
 Bibliotecas de tipo descrevem as características de objetos COM, como nomes de membros e tipos de dados. Manifestos de assembly executam a mesma função para [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplicativos. Eles incluem informações sobre o seguinte:  
  
-   Identidade do assembly, versão, cultura e assinatura digital.  
  
-   Arquivos que compõem a implementação do assembly.  
  
-   Tipos e recursos que compõem o assembly. Isso inclui aqueles que são exportados a partir dele.  
  
-   Dependências de tempo de compilação em outros assemblies.  
  
-   Permissões necessárias para o assembly ser executado corretamente.  
  
 Para obter mais informações sobre assemblies de manifestos de assembly, consulte [Assemblies no .NET](../../../standard/assembly/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>Importando e exportando as bibliotecas de tipos  
 O Visual Studio contém um utilitário, Tlbimp, que lhe permite importar informações de uma biblioteca de tipos em um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplicativo. Você pode gerar bibliotecas de tipos de assemblies usando o utilitário Tlbexp.  
  
 Para obter informações sobre como Tlbimp e Tlbexp, consulte [Tlbimp.exe (importador da biblioteca)](../../../framework/tools/tlbimp-exe-type-library-importer.md) e [Tlbexp.exe (exportador da biblioteca)](../../../framework/tools/tlbexp-exe-type-library-exporter.md).  
  
## <a name="interop-assemblies"></a>Assemblies de interoperabilidade  
 Assemblies de interoperabilidade são [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies que a ponte entre gerenciados e de código, membros de objeto COM mapeamento equivalente [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] gerenciados membros. Assemblies de interoperabilidade criados pelo Visual Basic .NET lidar com muitos dos detalhes de como trabalhar com objetos COM, como o marshaling de interoperabilidade.  
  
## <a name="interoperability-marshaling"></a>Marshaling de interoperabilidade  
 Todos os [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplicativos compartilham um conjunto de tipos comuns que permitem a interoperabilidade de objetos, independentemente da linguagem de programação que é usado. Os parâmetros e valores de retorno de objetos COM, às vezes, use tipos de dados que diferem daqueles usados no código gerenciado. *Marshaling de interoperabilidade* é o processo de compactação parâmetros e valores de retorno em tipos de dados equivalentes quando eles passam para e de objetos COM. Para obter mais informações, consulte [Marshaling de interoperabilidade](../../../framework/interop/interop-marshaling.md).  
  
## <a name="see-also"></a>Consulte também

- [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Passo a passo: implementação de herança com objetos COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Interoperação com código não gerenciado](../../../framework/interop/index.md)
- [Solução de problemas de Interoperabilidade](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
- [Assemblies no .NET](../../../standard/assembly/index.md)
- [Tlbimp.exe (Importador de Biblioteca de Tipos)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (Exportador de Biblioteca de Tipos)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Marshaling de interoperabilidade](../../../framework/interop/interop-marshaling.md)
- [Interoperabilidade COM sem registro](../../../framework/interop/registration-free-com-interop.md)
