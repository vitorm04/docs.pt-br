---
title: Solucionando problemas de interoperabilidade (Visual Basic) | Documentos do Microsoft
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
- interop, deploying assemblies
- assemblies [Visual Basic]
- interop, installing assemblies that share components
- COM objects, troubleshooting
- interop, sharing components
- troubleshooting interoperability
- interoperability, troubleshooting
- COM interop, troubleshooting
- assemblies [Visual Basic], deploying
- troubleshooting Visual Basic, interoperability
- interop assemblies
- interoperability, sharing components
- shared components, using with assemblies
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
caps.latest.revision: 21
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
ms.openlocfilehash: cbc37638ed5c57b94356c2d189f36b66202ceba5
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-interoperability-visual-basic"></a>Solucionando problemas de interoperabilidade (Visual Basic)
Quando você interoperar entre o código gerenciado do e COM o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], você pode encontrar um ou mais dos seguintes problemas comuns.  
  
##  <a name="vbconinteroperabilitymarshalinganchor1"></a>Marshaling de interoperabilidade  
 Às vezes, você talvez precise usar tipos de dados que não são parte do [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]. Assemblies de interoperabilidade tratam a maior parte do trabalho para objetos COM, mas você pode ter que controlar os tipos de dados que são usados quando os objetos gerenciados são expostos para COM. Por exemplo, estruturas de bibliotecas de classe devem especificar o `BStr` não gerenciado tipo em cadeias de caracteres enviados para objetos COM criados pelo Visual Basic 6.0 e versões anteriores. Nesses casos, você pode usar o <xref:System.Runtime.InteropServices.MarshalAsAttribute>atributo para fazer com que tipos gerenciados deve ser exposta como tipos não gerenciados.</xref:System.Runtime.InteropServices.MarshalAsAttribute>  
  
##  <a name="vbconinteroperabilitymarshalinganchor2"></a>Exportar cadeias de caracteres de comprimento fixo para código não gerenciado  
 No Visual Basic 6.0 e versões anteriores, cadeias de caracteres são exportadas para objetos COM como sequências de bytes sem um caractere de terminação nula. Para compatibilidade com outras linguagens, [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] inclui um caractere de finalização ao exportar cadeias de caracteres. A melhor maneira de resolver essa incompatibilidade é exportar cadeias de caracteres que não têm o caractere de terminação como matrizes de `Byte` ou `Char`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor3"></a>Exportando hierarquias de herança  
 Gerenciado classe hierarquias Nivelar out quando exposto como objetos COM. Por exemplo, se você define uma classe base com um membro e, em seguida, herda a classe base em uma classe derivada que é exposta como um objeto COM, os clientes que usam a classe derivada do objeto COM não será capazes de usar os membros herdados. Membros da classe base podem ser acessados de objetos apenas como instâncias de uma classe base e somente se a classe base também é criada como um objeto COM.  
  
## <a name="overloaded-methods"></a>Métodos Sobrecarregados  
 Embora você possa criar sobrecarregado métodos com [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], eles não são suportados pelo COM. Quando uma classe que contém métodos sobrecarregados é exposta como um objeto COM, os novos nomes de método são gerados para os métodos sobrecarregados.  
  
 Por exemplo, considere uma classe que tem duas sobrecargas de `Synch` método. Quando a classe é exposta como um objeto COM, os novos nomes de método gerado pode ser `Synch` e `Synch_2`.  
  
 A mudança de nome pode causar problemas de dois para os consumidores do objeto COM.  
  
1.  Clientes não podem esperar que os nomes de método gerado.  
  
2.  Os nomes de método gerado na classe exposta como um objeto COM podem alterar quando novas sobrecargas são adicionadas à classe ou sua classe base. Isso pode causar problemas de controle de versão.  
  
 Para solucionar os dois problemas, dê a cada método um nome exclusivo, em vez de usar a sobrecarga, quando você desenvolve objetos que serão expostos como objetos COM.  
  
##  <a name="vbconinteroperabilitymarshalinganchor4"></a>Uso de objetos COM por meio de Assemblies de interoperabilidade  
 Use assemblies de interoperabilidade quase como se fossem substituições de código gerenciado para os objetos COM que eles representam. No entanto, como eles são wrappers e não os objetos COM, há algumas diferenças entre usar assemblies de interoperabilidade e assemblies padrão. Essas áreas de diferença incluem a exposição de classes e tipos de dados de parâmetros e valores de retorno.  
  
##  <a name="vbconinteroperabilitymarshalinganchor5"></a>Classes expostas como ambas as Interfaces e Classes  
 Diferentemente das classes em assemblies padrão, classes COM são expostas em assemblies de interoperabilidade como uma interface e uma classe que representa a classe COM. Nome da interface é idêntica da classe COM. O nome da classe de interoperabilidade é o mesmo que a classe de COM original, mas com a palavra "Class" acrescentada. Por exemplo, suponha que você tenha um projeto com uma referência a um assembly de interoperabilidade para um objeto COM. Se o nome da classe COM `MyComClass`, IntelliSense e o Pesquisador de objetos mostram uma interface nomeada `MyComClass` e uma classe chamada `MyComClassClass`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor6"></a>Criação de instâncias de uma classe do .NET Framework  
 Geralmente, você cria uma instância de um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] classe usando o `New` instrução com um nome de classe. Ter uma classe COM representado por um assembly de interoperabilidade é o único caso em que você pode usar o `New` instrução com uma interface. Se você estiver usando a classe COM um `Inherits` instrução, você pode usar a interface como faria com uma classe. O código a seguir demonstra como criar um `Command` objeto em um projeto que tem uma referência ao objeto COM da biblioteca do Microsoft ActiveX Data objetos 2.8:  
  
 [!code-vb[20 VbVbalrInterop](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_1.vb)]  
  
 No entanto, se você estiver usando a classe COM como a base para uma classe derivada, você deve usar a classe de interoperabilidade que representa a classe COM, como no seguinte código:  
  
 [!code-vb[VbVbalrInterop&#21;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_2.vb)]  
  
> [!NOTE]
>  Assemblies de interoperabilidade implicitamente implementam interfaces que representam classes COM. Você não deve tentar usar o `Implements` resultará instrução para implementar essas interfaces ou um erro.  
  
##  <a name="vbconinteroperabilitymarshalinganchor7"></a>Tipos de dados de parâmetros e valores de retorno  
 Ao contrário de membros de conjuntos padrão, os membros de assembly de interoperabilidade podem ter tipos de dados que diferem daqueles usados na declaração do objeto original. Embora os assemblies de interoperabilidade convertem implicitamente tipos COM compatível tipos common language runtime, você deve prestar atenção aos tipos de dados que são usados por ambos os lados para evitar erros de tempo de execução. Por exemplo, em objetos COM criados no Visual Basic 6.0 e versões anteriores, os valores do tipo `Integer` pressupõem o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] tipo equivalente, `Short`. É recomendável que você use o Pesquisador de objetos para examinar as características de membros importados antes de você usá-los.  
  
##  <a name="vbconinteroperabilitymarshalinganchor8"></a>Métodos COM nível de módulo  
 A maioria dos objetos são usados, criando uma instância de uma classe de COM usando o `New` palavra-chave e, em seguida, chamar métodos do objeto. Uma exceção a essa regra envolve objetos que contêm `AppObj` ou `GlobalMultiUse` classes COM. Essas classes se parecer com métodos de nível de módulo em [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] classes. Visual Basic 6.0 e versões anteriores implicitamente criam instâncias desses objetos para você na primeira vez que você chama um dos seus métodos. Por exemplo, no Visual Basic 6.0 você pode adicionar uma referência para a biblioteca de objetos do Microsoft DAO 3.6 e chamar o `DBEngine` método sem primeiro criar uma instância:  
  
```  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]requer que você sempre crie instâncias de objetos COM antes de poder usar seus métodos. Para usar esses métodos em [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)], declare uma variável de classe desejado e use a nova palavra-chave para atribuir o objeto para a variável de objeto. O `Shared` palavra-chave pode ser usado quando você deseja garantir que apenas uma instância da classe é criada.  
  
 [!code-vb[VbVbalrInterop&#23;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_3.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor9"></a>Erros não tratados em manipuladores de eventos  
 Um problema de interoperabilidade comum envolve erros nos manipuladores de eventos que tratam os eventos gerados por objetos COM. Esses erros são ignorados a menos que especificamente Verifique erros usando `On Error` ou `Try...Catch...Finally` instruções. Por exemplo, o exemplo a seguir é de um [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] projeto que tem uma referência ao objeto objetos de dados do Microsoft ActiveX 2.8 biblioteca COM.  
  
 [!code-vb[VbVbalrInterop&#24;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_4.vb)]  
  
 Este exemplo gera um erro conforme o esperado. No entanto, se você tentar o mesmo exemplo sem o `Try...Catch...Finally` bloco, o erro será ignorado como se você usou o `OnError Resume Next` instrução. Sem tratamento de erros, a divisão por zero falhará silenciosamente. Como esses erros nunca geram erros de exceção sem tratamento, é importante que você usa alguma forma de tratamento de exceções em manipuladores de eventos para manipular eventos de objetos COM.  
  
### <a name="understanding-com-interop-errors"></a>Noções básicas sobre erros de interoperabilidade de COM  
 Sem tratamento de erros, chamadas de interoperabilidade com frequência geram erros que forneçam pouca informação. Sempre que possível, use estruturado tratamento de erro para fornecer mais informações sobre problemas quando eles ocorrerem. Isso pode ser especialmente útil ao depurar aplicativos. Por exemplo:  
  
 [!code-vb[25 VbVbalrInterop](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_5.vb)]  
  
 Você pode encontrar informações como a descrição do erro, HRESULT e a origem de erros COM examinando o conteúdo do objeto de exceção.  
  
##  <a name="vbconinteroperabilitymarshalinganchor10"></a>Problemas de controle ActiveX  
 A maioria dos controles ActiveX que funcionam com o Visual Basic 6.0 funciona com [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] sem problemas. As principais exceções são controles de contêiner ou controles que contêm visualmente outros controles. Alguns exemplos de controles mais antigos que não funcionam corretamente com [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] são os seguintes:  
  
-   Controle quadro do Microsoft Forms 2.0  
  
-   Controle acima-abaixo, também conhecido como o controle de rotação  
  
-   Controle de guia Sheridan  
  
 Há apenas algumas soluções alternativas para problemas de controle ActiveX sem suporte. Você pode migrar os controles existentes a [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] se você possui o código-fonte original. Caso contrário, você pode verificar com fornecedores de software para atualizado. Compatível com .NET versões dos controles para substituir sem suporte a controles ActiveX.  
  
##  <a name="vbconinteroperabilitymarshalinganchor11"></a>Passando ReadOnly propriedades de controles ByRef  
 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]às vezes gera erros COM, como "Erro 0x800A017F CTL_E_SETNOTSUPPORTED" quando você passa `ReadOnly` propriedades de alguns controles ActiveX antigos como `ByRef` parâmetros para outros procedimentos. Chamadas de procedimento semelhante do Visual Basic 6.0 não geram um erro e os parâmetros são tratados como se você os passado por valor. A mensagem de erro que você vê na [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] é o objeto COM relatórios que você está tentando alterar uma propriedade que não tem uma propriedade `Set` procedimento.  
  
 Se você tiver acesso ao procedimento que está sendo chamado, você pode evitar esse erro, usando o `ByVal` palavra-chave para declarar parâmetros que aceitam `ReadOnly` propriedades. Por exemplo:  
  
 [!code-vb[VbVbalrInterop&#26;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_6.vb)]  
  
 Se você não tiver acesso ao código-fonte para o procedimento que está sendo chamado, você pode forçar a propriedade a ser passado por valor, adicionando um conjunto extra de procedimento de chamada entre colchetes. Por exemplo, em um projeto que tem uma referência ao objeto COM da biblioteca do Microsoft ActiveX Data objetos 2.8, você pode usar:  
  
 [!code-vb[VbVbalrInterop&#27;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_7.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor12"></a>Implantando Assemblies que expõem a interoperabilidade  
 Implantando assemblies que expõem interfaces COM apresenta alguns desafios exclusivos. Por exemplo, um problema potencial ocorre quando o mesmo assembly COM referenciam a aplicativos separados. Essa situação é comum quando uma nova versão de um assembly é instalada e outro aplicativo ainda está usando a versão antiga do assembly. Se você desinstalar um assembly que compartilha uma DLL, você pode, inadvertidamente, tornar disponível para os outros assemblies.  
  
 Para evitar esse problema, você deve instalar assemblies compartilhados para o Cache de Assembly Global (GAC) e usar um MergeModule para o componente. Se você não pode instalar o aplicativo no GAC, ele deve ser instalado para CommonFilesFolder em um subdiretório específico da versão.  
  
 Assemblies que não são compartilhados devem estar localizados no diretório com o aplicativo de chamada lado a lado.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute></xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Tlbimp.exe (importador de biblioteca)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)   
 [Tlbexp.exe (exportador da biblioteca)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)   
 [Passo a passo: Implementando a herança com objetos COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Cache de Assembly Global](http://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202)
