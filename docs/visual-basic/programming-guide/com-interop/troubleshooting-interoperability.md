---
title: Solucionando problemas de interoperabilidade (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop, deploying assemblies
- assemblies [Visual Basic]
- interop, installing assemblies that share components
- COM objects, troubleshooting
- interop, sharing components
- troubleshooting interoperability [Visual Basic]
- interoperability, troubleshooting
- COM interop [Visual Basic], troubleshooting
- assemblies [Visual Basic], deploying
- troubleshooting Visual Basic, interoperability
- interop assemblies
- interoperability, sharing components
- shared components, using with assemblies
ms.assetid: b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37
ms.openlocfilehash: 5b92eaf56e337b8a8128bb3a0706ecdb76177c0e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516821"
---
# <a name="troubleshooting-interoperability-visual-basic"></a>Solucionando problemas de interoperabilidade (Visual Basic)
Quando você interoperar entre o código gerenciado do e COM o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], você pode encontrar um ou mais dos seguintes problemas comuns.  
  
##  <a name="vbconinteroperabilitymarshalinganchor1"></a> Marshaling de interoperabilidade  
 Às vezes, você talvez precise usar tipos de dados que não são parte do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Assemblies de interoperabilidade lidar com a maioria do trabalho para objetos COM, mas talvez você precise controlar os tipos de dados que são usados quando os objetos gerenciados são expostos COM. Por exemplo, as estruturas em bibliotecas de classe devem especificar o `BStr` tipo em cadeias de caracteres enviados para objetos COM criados pelo Visual Basic 6.0 e versões anteriores não gerenciado. Nesses casos, você pode usar o <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo para fazer com que tipos gerenciados deve ser exposta como tipos não gerenciados.  
  
##  <a name="vbconinteroperabilitymarshalinganchor2"></a> Exportando cadeias de caracteres de comprimento fixo para código não gerenciado  
 No Visual Basic 6.0 e versões anteriores, as cadeias de caracteres são exportadas para objetos COM como sequências de bytes sem um caractere de terminação nula. Para compatibilidade com outras linguagens, o Visual Basic .NET inclui um caractere de terminação ao exportar as cadeias de caracteres. A melhor maneira de resolver essa incompatibilidade é exportar cadeias de caracteres que não têm o caractere de encerramento como matrizes de `Byte` ou `Char`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor3"></a> Exportação de hierarquias de herança  
 Classe hierarquias Nivelar out quando exposto como objetos COM gerenciada. Por exemplo, se você define uma classe base com um membro e, em seguida, herda a classe base em uma classe derivada que é exposta como um objeto COM, os clientes que usam a classe derivada no objeto COM não será capazes de usar os membros herdados. Membros da classe base podem ser acessados de objetos COM apenas como instâncias de uma classe base e, em seguida, somente se a classe base também é criada como um objeto COM.  
  
## <a name="overloaded-methods"></a>Métodos Sobrecarregados  
 Embora você possa criar métodos sobrecarregados com o Visual Basic, eles não são suportados pelo COM. Quando uma classe que contém os métodos sobrecarregados é exposta como um objeto COM, os novos nomes de método são gerados para os métodos sobrecarregados.  
  
 Por exemplo, considere uma classe que tem duas sobrecargas do `Synch` método. Quando a classe é exposta como um objeto COM, os novos nomes de método gerado pode ser `Synch` e `Synch_2`.  
  
 A renomeação pode causar problemas de duas para os consumidores do objeto COM.  
  
1.  Os clientes não podem esperar que os nomes de método gerado.  
  
2.  Os nomes de método gerado na classe exposta como um objeto COM podem mudar quando novas sobrecargas são adicionadas à classe ou sua classe base. Isso pode causar problemas de controle de versão.  
  
 Para resolver os dois problemas, dê a cada método um nome exclusivo, em vez de usar a sobrecarga, quando você desenvolve os objetos que serão expostos como objetos COM.  
  
##  <a name="vbconinteroperabilitymarshalinganchor4"></a> Uso de objetos COM por meio de Assemblies de interoperabilidade  
 Você usar assemblies de interoperabilidade, quase como se eles são substituições de código gerenciado para os objetos COM que eles representam. No entanto, como elas são wrappers e objetos não reais de objetos, há algumas diferenças entre usar assemblies de interoperabilidade e assemblies padrão. Essas áreas de diferença incluem a exposição das classes e tipos de dados para parâmetros e valores de retorno.  
  
##  <a name="vbconinteroperabilitymarshalinganchor5"></a> Classes expostas como ambas as Interfaces e Classes  
 Diferentemente das classes em assemblies padrão, as classes COM são expostas em assemblies de interoperabilidade como uma interface e uma classe que representa a classe COM. Nome da interface é idêntica da classe COM. O nome da classe interoperabilidade é o mesmo da classe COM original, mas com a palavra "Class" acrescentado. Por exemplo, suponha que você tenha um projeto com uma referência a um assembly de interoperabilidade para um objeto COM. Se o nome da classe COM `MyComClass`, IntelliSense e o Pesquisador de objetos mostram uma interface denominada `MyComClass` e uma classe chamada `MyComClassClass`.  
  
##  <a name="vbconinteroperabilitymarshalinganchor6"></a> Criação de instâncias de uma classe do .NET Framework  
 Em geral, você cria uma instância de um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classe usando o `New` instrução com um nome de classe. Ter uma classe COM representado por um assembly de interoperabilidade é o único caso em que você pode usar o `New` instrução com uma interface. A menos que você estiver usando a classe COM um `Inherits` instrução, você pode usar a interface exatamente como faria com uma classe. O código a seguir demonstra como criar um `Command` objeto em um projeto que tem uma referência para o objeto de objetos de dados do Microsoft ActiveX 2.8 biblioteca COM:  
  
 [!code-vb[VbVbalrInterop#20](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_1.vb)]  
  
 No entanto, se você estiver usando a classe COM como a base para uma classe derivada, você deve usar a classe de interoperabilidade que representa a classe COM, como no código a seguir:  
  
 [!code-vb[VbVbalrInterop#21](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_2.vb)]  
  
> [!NOTE]
>  Assemblies de interoperabilidade implicitamente implementam interfaces que representam classes COM. Você não deve tentar usar o `Implements` resultará instrução para implementar essas interfaces ou um erro.  
  
##  <a name="vbconinteroperabilitymarshalinganchor7"></a> Tipos de dados para parâmetros e valores de retorno  
 Ao contrário de membros de assemblies padrão, os membros do assembly de interoperabilidade podem ter tipos de dados que são diferentes daqueles usados na declaração do objeto original. Embora os assemblies de interoperabilidade se convertem implicitamente tipos COM compatível tipos common language runtime, você deve prestar atenção aos tipos de dados que são usados por ambos os lados para evitar erros de tempo de execução. Por exemplo, em objetos COM criados no Visual Basic 6.0 e versões anteriores, os valores do tipo `Integer` supor que o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] tipo equivalente, `Short`. É recomendável que você use o Pesquisador de objetos para examinar as características de membros importados antes de você usá-los.  
  
##  <a name="vbconinteroperabilitymarshalinganchor8"></a> Métodos de COM de nível de módulo  
 A maioria dos objetos COM são usadas, criando uma instância de uma classe de COM usando o `New` palavra-chave e, em seguida, chamar métodos do objeto. Uma exceção a essa regra envolve a objetos COM que contêm `AppObj` ou `GlobalMultiUse` classes COM. Essas classes são semelhantes a métodos de nível de módulo em classes do Visual Basic .NET. Visual Basic 6.0 e versões anteriores implicitamente criar instâncias desses objetos para você na primeira vez que você chame um dos seus métodos. Por exemplo, no Visual Basic 6.0 você pode adicionar uma referência ao objeto de biblioteca do Microsoft DAO 3.6 e chame o `DBEngine` método sem primeiro criar uma instância:  
  
```vb  
Dim db As DAO.Database  
' Open the database.  
Set db = DBEngine.OpenDatabase("C:\nwind.mdb")  
' Use the database object.  
```  
  
 Visual Basic .NET exige que você sempre criar instâncias de objetos COM antes de poder usar seus métodos. Para usar esses métodos no Visual Basic, declare uma variável de classe desejada e use a nova palavra-chave para atribuir o objeto para a variável de objeto. O `Shared` palavra-chave pode ser usado quando você deseja garantir que apenas uma instância da classe é criada.  
  
 [!code-vb[VbVbalrInterop#23](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_3.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor9"></a> Erros sem tratamento em manipuladores de eventos  
 Um problema de interoperabilidade comum envolve erros em manipuladores de eventos que tratam os eventos gerados por objetos COM. Esses erros são ignorados, a menos que especificamente procurar erros usando `On Error` ou `Try...Catch...Finally` instruções. Por exemplo, o exemplo a seguir é de um projeto do Visual Basic .NET que tem uma referência para o objeto de objetos de dados do Microsoft ActiveX 2.8 biblioteca COM.  
  
 [!code-vb[VbVbalrInterop#24](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_4.vb)]  
  
 Este exemplo gera um erro, conforme o esperado. No entanto, se você tentar o mesmo exemplo sem o `Try...Catch...Finally` bloco, o erro será ignorado como se você usou o `OnError Resume Next` instrução. A divisão por zero silenciosamente falhará sem tratamento de erros. Como esses erros nunca geram uma exceção sem tratamento de erros, é importante que você usa alguma forma de tratamento de exceções em manipuladores de eventos que tratam os eventos dos objetos COM.  
  
### <a name="understanding-com-interop-errors"></a>Noções básicas sobre erros de interoperabilidade COM  
 Sem tratamento de erros, chamadas de interoperabilidade geralmente geram erros que forneçam pouca informação. Sempre que possível, use o tratamento estruturado para fornecer mais informações sobre problemas quando eles ocorrerem. Isso pode ser especialmente útil ao depurar aplicativos. Por exemplo:  
  
 [!code-vb[VbVbalrInterop#25](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_5.vb)]  
  
 Você pode encontrar informações como a descrição do erro, HRESULT e a fonte de erros COM examinando o conteúdo do objeto de exceção.  
  
##  <a name="vbconinteroperabilitymarshalinganchor10"></a> Problemas de controle ActiveX  
 A maioria dos controles ActiveX que funcionam com o Visual Basic 6.0 funcionam com o Visual Basic .NET sem problemas. As principais exceções são controles de contêiner ou controles que contêm visualmente outros controles. Alguns exemplos de controles mais antigos que não funcionam corretamente com o Visual Studio são da seguinte maneira:  
  
-   Controle quadro do Microsoft Forms 2.0  
  
-   Controle de cima para baixo, também conhecido como o controle de rotação  
  
-   Controle de guia Sheridan  
  
 Há apenas algumas soluções alternativas para problemas de controle ActiveX sem suporte. Você pode migrar os controles existentes para o Visual Studio se você possui o código-fonte original. Caso contrário, você pode verificar com fornecedores de software para atualizado. Compatível com .NET versões dos controles para substituir sem suporte a controles ActiveX.  
  
##  <a name="vbconinteroperabilitymarshalinganchor11"></a> Passando propriedades de somente leitura de controles ByRef  
 Visual Basic .NET gera erros COM, como "CTL_E_SETNOTSUPPORTED de 0x800A017F de erro", às vezes, quando você passa `ReadOnly` propriedades de alguns controles ActiveX mais antigos como `ByRef` parâmetros para outros procedimentos. Chamadas de procedimento semelhante do Visual Basic 6.0 gerará um erro e os parâmetros são tratados como se você os passados por valor. A mensagem de erro do Visual Basic .NET indica que você está tentando alterar uma propriedade que não tem uma propriedade `Set` procedimento.  
  
 Se você tiver acesso ao procedimento sendo chamado, você pode evitar esse erro, usando o `ByVal` palavra-chave para declarar parâmetros que aceitam `ReadOnly` propriedades. Por exemplo:  
  
 [!code-vb[VbVbalrInterop#26](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_6.vb)]  
  
 Se você não tiver acesso ao código-fonte para o procedimento sendo chamado, você pode forçar a propriedade a ser passado por valor, adicionando um conjunto extra de parênteses em torno do procedimento de chamada. Por exemplo, em um projeto que tem uma referência para o objeto de objetos de dados do Microsoft ActiveX 2.8 biblioteca COM, você pode usar:  
  
 [!code-vb[VbVbalrInterop#27](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/troubleshooting-interoperability_7.vb)]  
  
##  <a name="vbconinteroperabilitymarshalinganchor12"></a> Implantando Assemblies que expõem a interoperabilidade  
 Implantando assemblies que expõem interfaces COM apresenta alguns desafios únicos. Por exemplo, um problema potencial ocorre quando o mesmo assembly COM referência a aplicativos separados. Essa situação é comum quando uma nova versão de um assembly é instalada e o outro aplicativo ainda está usando a versão antiga do assembly. Se você desinstalar um assembly que compartilha uma DLL, você pode, inadvertidamente, torna indisponível para os outros assemblies.  
  
 Para evitar esse problema, você deve instalar assemblies compartilhados para Cache de Assembly Global (GAC) e usar um MergeModule para o componente. Se você não pode instalar o aplicativo no GAC, ele deve ser instalado para Pastaarqscomuns em um subdiretório específico de versão.  
  
 Assemblies que não são compartilhados devem estar localizados, lado a lado no diretório com o aplicativo de chamada.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (Importador de Biblioteca de Tipos)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (Exportador de Biblioteca de Tipos)](https://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Instruções passo a passo: implementando a herança com objetos COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Cache de assembly global](../../../framework/app-domains/gac.md)
