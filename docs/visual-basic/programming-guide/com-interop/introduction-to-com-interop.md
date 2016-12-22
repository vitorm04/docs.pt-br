---
title: "Introdu&#231;&#227;o &#224; interoperabilidade COM (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "interoperabilidade COM, sobre a interoperabilidade COM"
  - "assemblies de interoperabilidade"
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Introdu&#231;&#227;o &#224; interoperabilidade COM (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O Modelo de Objeto Componente \(COM\) permite a um objeto expor sua funcionalidade a outros componentes e hospedar aplicações.  Enquanto COM objetos foram fundamentais para o Windows programação por muitos anos, aplicativos criados para o Common Language Runtime \(CLR\) oferecem várias vantagens.  
  
 Aplicativos [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] eventualmente substituirão aqueles desenvolvidos com COM.  Até então, talvez você precise usar ou criar objetos COM usando [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)].  Interoperabilidade com COM, ou  *interoperabilidade COM* , permite que você use objetos COM existentes ao fazer a transição para o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] no seu próprio ritmo.  
  
 Usando o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] para criar componentes COM, você pode usar Registration\-Free interoperabilidade COM.  Isso permite que você controle qual versão de DLL é ativada quando mais de uma versão é instalada em um computador e permite que os usuários finais Use xcopy ou FTP para copiar seu aplicativo para um diretório apropriado no computador onde ele pode ser executado.  Para obter mais informações, consulte [Interoperabilidade COM sem registro](../Topic/Registration-Free%20COM%20Interop.md).  
  
## Código gerenciado e dados  
 O código desenvolvido para o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] é mencionado como  *código gerenciado*  e contém metadados que é usado pelo CLR.  Dados usados por aplicativos [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] são chamados  *dados gerenciados*  porque o tempo de execução gerencia dados relacionados a tarefas como alocar recuperar memória e executar uma verificação de tipo.  Por padrão, [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] usa código gerenciado e dados, mas você pode acessar a código não gerenciado e dados de objetos COM usando os módulos de interoperabilidade \(descritos posteriormente nessa página\).  
  
## Conjuntos de Módulos \(Assemblies\)  
 Um conjunto é o principal bloco de construção de um aplicativo [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].  Ele é uma coleção de funcionalidade que é criado, versionados e implantada como uma unidade de implementação única que contém um ou mais arquivos.  Cada assembly contém um manifesto do assembly.  
  
## Bibliotecas tipo e manifestos assembly  
 Bibliotecas de tipos descrever características de COM objetos, como nomes de membros e tipos de dados.  Manifestos assembly executam a mesma função de aplicativos [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] .  Eles incluem informações sobre o seguinte:  
  
-   Identidade assembly, versão, cultura e assinatura digital.  
  
-   Arquivos que constituem a implementação de assembly.  
  
-   Tipos e recursos que constituem o assembly.  Isto inclui aqueles que são exportados a partir deste.  
  
-   Dependências de tempo de compilação em outros assemblies.  
  
-   Permissões necessárias para o assembly funcionar corretamente.  
  
 Para obter mais informações sobre assemblies de manifestos de assembly, consulte [Assemblies e o cache de assemblies global](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md).  
  
### Importando e exportando bibliotecas de tipos  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] contém um utilitário, Tlbimp, que permite que você importar informações de uma biblioteca de tipos para um aplicativo[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] .  Você pode gerar bibliotecas de tipos a partir de assemblies usando o utilitário TlbExp.  
  
 Para obter informações sobre como Tlbimp e TlbExp, consulte [Tlbimp.exe \(Importador de Biblioteca de Tipos\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md) e [Tlbexp.exe \(Exportador de Biblioteca de Tipos\)](../Topic/Tlbexp.exe%20\(Type%20Library%20Exporter\).md).  
  
## Assemblies de interoperabilidade  
 Assemblies Interop são assemblies [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] que transpõem entre códigos gerenciados e não gerenciados, mapeando membros COM de objeto a membros [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] gerenciados equivalentes.  Assemblies Interop criados pelo [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] manipulam muitos dos detalhes de trabalhar com objetos COM, como a organização de interoperabilidade.  
  
## Interoperabilidade Marshaling  
 Todos os aplicativos [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] compartilham um conjunto de tipos comuns que permitem a interoperabilidade do objetos, independentemente da linguagem de programação que é usado.  Os parâmetros e valores de retorno de COM objetos às vezes usam tipos de dados que diferem daqueles usados no código gerenciado.  *Marshaling deInteroperabilidade*  é o processo de compactação parâmetros e valores de retorno em tipos de dados equivalente à medida que eles movam para e de objetos COM.  Para obter mais informações, consulte [Realizando marshaling de interoperabilidade](../Topic/Interop%20Marshaling.md).  
  
## Consulte também  
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Instruções passo a passo: implementando a herança com objetos COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Interoperação com código não gerenciado](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Solucionando problemas de interoperabilidade](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)   
 [Assemblies e o cache de assemblies global](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Tlbimp.exe \(Importador de Biblioteca de Tipos\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)   
 [Tlbexp.exe \(Exportador de Biblioteca de Tipos\)](../Topic/Tlbexp.exe%20\(Type%20Library%20Exporter\).md)   
 [Realizando marshaling de interoperabilidade](../Topic/Interop%20Marshaling.md)   
 [Interoperabilidade COM sem registro](../Topic/Registration-Free%20COM%20Interop.md)