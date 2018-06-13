---
title: Introdução à interoperabilidade COM (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: 639b621215f25bc1042274a92a21fca2985e5918
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644388"
---
# <a name="introduction-to-com-interop-visual-basic"></a>Introdução à interoperabilidade COM (Visual Basic)
O modelo de objeto de componente (COM) permite que um objeto expor sua funcionalidade a outros componentes e aplicativos do host. Enquanto COM objetos foram fundamentais para o Windows programação por muitos anos, aplicativos criados para o common language runtime (CLR) oferecem muitas vantagens.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplicativos eventualmente substituirão aqueles desenvolvidos com. Até lá, você terá que usar ou criar objetos COM usando o Visual Studio. Interoperabilidade com, ou *interoperabilidade*, permite que você use objetos COM existentes ao fazer a transição para o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] em seu próprio ritmo.  
  
 Usando o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] para criar componentes COM, você pode usar a interoperação COM sem registro. Isso lhe permite controlar qual versão DLL é ativada quando mais de uma versão é instalada em um computador e permite que os usuários finais use XCOPY ou FTP para copiar seu aplicativo para um diretório apropriado no computador onde ele pode ser executado. Para obter mais informações, consulte [interoperação COM sem registro](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd).  
  
## <a name="managed-code-and-data"></a>O código gerenciado e dados  
 O código desenvolvido para o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] é conhecido como *código gerenciado*e contém metadados que é usado pelo CLR. Dados usados pelo [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplicativos é chamado *dados gerenciados* porque o tempo de execução gerencia as tarefas relacionadas a dados, como alocar recuperar memória e executar verificação de tipo. Por padrão, o Visual Basic .NET usa código gerenciado e os dados, mas você pode acessar o código não gerenciado e dados de objetos COM usando assemblies de interoperabilidade (descritos posteriormente nesta página).  
  
## <a name="assemblies"></a>Assemblies  
 Um assembly é o principal bloco de construção de um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplicativo. É uma coleção de funcionalidade que é criada, com controle de versão e implantado como uma unidade de implementação única que contém um ou mais arquivos. Cada assembly contém um manifesto do assembly.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Manifestos de Assembly e bibliotecas de tipo  
 Bibliotecas de tipo descrevem características de objetos, como nomes de membros e tipos de dados. Manifestos assembly executam a mesma função [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplicativos. Eles incluem informações sobre o seguinte:  
  
-   Identidade do assembly, versão, cultura e assinatura digital.  
  
-   Arquivos que compõem a implementação do assembly.  
  
-   Tipos e recursos que compõem o assembly. Isso inclui aquelas que são exportados dele.  
  
-   Dependências de tempo de compilação em outros assemblies.  
  
-   Permissões necessárias para o assembly seja executado corretamente.  
  
 Para obter mais informações sobre assemblies de manifestos de assembly, consulte [Assemblies e Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>Importando e exportando bibliotecas de tipo  
 O Visual Studio contém um utilitário Tlbimp, que lhe permite importar informações de uma biblioteca de tipos em um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplicativo. Você pode gerar bibliotecas de tipos de assemblies usando o utilitário Tlbexp.  
  
 Para obter informações sobre como Tlbimp e Tlbexp, consulte [Tlbimp.exe (importador da biblioteca)](../../../framework/tools/tlbimp-exe-type-library-importer.md) e [Tlbexp.exe (exportador da biblioteca)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d).  
  
## <a name="interop-assemblies"></a>Assemblies de interoperabilidade  
 Assemblies de interoperabilidade são [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies que ponte entre gerenciados e de código, membros do objeto COM mapeamento para equivalente [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] gerenciados. Assemblies de interoperabilidade criados pelo Visual Basic .NET lidar com muitos dos detalhes de como trabalhar com objetos COM, como a realização de marshaling de interoperabilidade.  
  
## <a name="interoperability-marshaling"></a>Marshaling de interoperabilidade  
 Todos os [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplicativos compartilham um conjunto de tipos comuns que permitem a interoperabilidade do objetos, independentemente da linguagem de programação que é usado. Os parâmetros e valores de retorno de objetos COM, às vezes, usam tipos de dados que diferem daqueles usados no código gerenciado. *Marshaling de interoperabilidade* é o processo de compactação parâmetros e valores de retorno em tipos de dados equivalentes, conforme se move para e de objetos COM. Para obter mais informações, consulte [Marshaling de interoperabilidade](../../../framework/interop/interop-marshaling.md).  
  
## <a name="see-also"></a>Consulte também  
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Instruções passo a passo: implementando a herança com objetos COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Interoperação com código não gerenciado](../../../framework/interop/index.md)  
 [Solução de problemas de Interoperabilidade](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Tlbimp.exe (Importador de Biblioteca de Tipos)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (Exportador de Biblioteca de Tipos)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Marshaling de interoperabilidade](../../../framework/interop/interop-marshaling.md)  
 [Interoperabilidade COM sem registro](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)
