---
title: "Introdução à interoperabilidade COM (Visual Basic) | Documentos do Microsoft"
ms.custom: 
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
- interop assemblies
- COM interop, about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 8866dbadca040c57ed2b59540dd2c341eb81758c
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-com-interop-visual-basic"></a>Introdução à interoperabilidade COM (Visual Basic)
O modelo de objeto de componente (COM) permite um objeto expor sua funcionalidade a outros componentes e aplicativos do host. Enquanto COM objetos foram fundamentais para o Windows programação por muitos anos, aplicativos criados para o common language runtime (CLR) oferecem muitas vantagens.  
  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]aplicativos eventualmente substituirão aqueles desenvolvidos com. Até lá, você talvez precise usar ou criar objetos COM usando [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]. Interoperabilidade com, ou *interoperabilidade*, permite que você use objetos COM existentes ao fazer a transição para o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] em seu próprio ritmo.  
  
 Usando o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] para criar componentes COM, você pode usar registration-free interoperabilidade COM. Isso lhe permite controlar qual versão DLL é ativada quando mais de uma versão é instalada em um computador e permite que os usuários finais use XCOPY ou FTP para copiar seu aplicativo para um diretório apropriado no computador onde ele pode ser executado. Para obter mais informações, consulte [Registration-Free interoperabilidade COM](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd).  
  
## <a name="managed-code-and-data"></a>Código gerenciado e dados  
 O código desenvolvido para o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] é conhecido como *código gerenciado*e contém metadados que é usado pelo CLR. Dados usados por [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] aplicativos é chamado *dados gerenciados* porque o tempo de execução gerencia tarefas relacionadas a dados, como alocar recuperar memória e executar verificação de tipo. Por padrão, [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] usa código gerenciado e dados, mas você pode acessar o código não gerenciado e dados de objetos COM usando assemblies de interoperabilidade (descritos posteriormente nesta página).  
  
## <a name="assemblies"></a>Assemblies  
 Um assembly é o principal bloco de construção de uma [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] aplicativo. É uma coleção de funcionalidade que é criado, versionados e implantada como uma unidade de implementação única que contém um ou mais arquivos. Cada assembly contém um manifesto do assembly.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Bibliotecas de tipo e manifestos Assembly  
 Bibliotecas de tipos descrevem características de objetos, como nomes de membros e tipos de dados. Manifestos assembly executam a mesma função [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] aplicativos. Eles incluem informações sobre o seguinte:  
  
-   Identidade do assembly, versão, cultura e assinatura digital.  
  
-   Arquivos que compõem a implementação do assembly.  
  
-   Tipos e recursos que compõem o assembly. Isso inclui aquelas que são exportados a partir deste.  
  
-   Dependências de tempo de compilação em outros assemblies.  
  
-   Permissões necessárias para o assembly seja executado corretamente.  
  
 Para obter mais informações sobre assemblies de manifestos de assembly, consulte [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>Importando e exportando bibliotecas de tipos  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]contém um utilitário, Tlbimp, que lhe permite importar informações de uma biblioteca de tipos em um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] aplicativo. Você pode gerar bibliotecas de tipos de assemblies usando o utilitário Tlbexp.  
  
 Para obter informações sobre como Tlbimp e Tlbexp, consulte [Tlbimp.exe (importador de biblioteca)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382) e [Tlbexp.exe (exportador da biblioteca)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d).  
  
## <a name="interop-assemblies"></a>Assemblies de interoperabilidade  
 Assemblies de interoperabilidade são [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] código de assemblies que ponte entre gerenciados e não gerenciados, membros do objeto COM mapeamento para equivalente [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] gerenciados. Assemblies de interoperabilidade criados pelo [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] manipular muitos dos detalhes de trabalhar com objetos COM, como o marshaling de interoperabilidade.  
  
## <a name="interoperability-marshaling"></a>Marshaling de interoperabilidade  
 Todos os [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] aplicativos compartilham um conjunto de tipos comuns que permitem a interoperabilidade do objetos, independentemente da linguagem de programação que é usado. Os parâmetros e valores de retorno de COM objetos às vezes usam tipos de dados que diferem daqueles usados no código gerenciado. *Marshaling de interoperabilidade* é o processo de compactação parâmetros e valores de retorno em tipos de dados equivalentes quando eles passam para e de objetos COM. Para obter mais informações, consulte [Interop Marshaling](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="see-also"></a>Consulte também  
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Passo a passo: Implementando a herança com objetos COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Interoperação com código não gerenciado](https://msdn.microsoft.com/library/sd10k43k)   
 [Solucionando problemas de interoperabilidade](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)   
 [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Tlbimp.exe (importador de biblioteca)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)   
 [Tlbexp.exe (exportador da biblioteca)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)   
 [Marshaling de interoperabilidade](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Interoperabilidade COM sem registro](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)
