---
title: "Instruções passo a passo: criando um aplicativo extensível"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [.NET Framework], add-in pipeline
- host-side adapters for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], creating
- add-in-side adapter [.NET Framework]
- contracts for add-in pipelines [.NET Framework]
ms.assetid: 694a33c5-a040-450d-aed5-ac49fc88ce61
caps.latest.revision: "32"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac4b6fc2ae36d848306178f281cceeeb0654ec03
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-extensible-application"></a>Instruções passo a passo: criando um aplicativo extensível
Este passo a passo descreve como criar um pipeline para um suplemento que executa funções de cálculo simples. Não demonstra um cenário do mundo real; em vez disso, ele demonstra a funcionalidade básica de um pipeline e como um suplemento pode fornecer serviços para um host.  
  
 Este passo a passo descreve as seguintes tarefas:  
  
-   Criando uma solução do Visual Studio.  
  
-   Criando a estrutura de diretórios do pipeline.  
  
-   Criar o contrato e modos de exibição.  
  
-   Criando o adaptador do lado do suplemento.  
  
-   Criando o adaptador do lado do host.  
  
-   Criando o host.  
  
-   Criando o suplemento.  
  
-   Implantando o pipeline.  
  
-   Executando o aplicativo de host.  
  
 Esse pipeline passa somente tipos serializáveis (<xref:System.Double> e <xref:System.String>), entre o host e o suplemento. Para obter um exemplo que mostra como passar coleções de tipos de dados complexos, consulte [passo a passo: passando coleções entre Hosts e suplementos](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5).  
  
 O contrato para este pipeline define um modelo de objeto de quatro operações aritméticas: adicionar, subtrair, multiplicar e dividir. O host fornece o suplemento com uma equação para calcular, como 2 + 2, e o suplemento retorna o resultado para o host.  
  
 Versão 2 do suplemento Calculadora fornece mais Calculando possibilidades e demonstra o controle de versão. Ela é descrita [passo a passo: Habilitando compatibilidade com versões anteriores, como alterações do seu Host](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes itens para concluir esta explicação:  
  
-   [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="creating-a-visual-studio-solution"></a>Criando uma solução do Visual Studio  
 Usar uma solução em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] para conter os projetos dos segmentos de pipeline.  
  
#### <a name="to-create-the-pipeline-solution"></a>Para criar a solução de pipeline  
  
1.  Em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], crie um novo projeto denominado `Calc1Contract`. Baseá-la no **biblioteca de classes** modelo.  
  
2.  Nome da solução `CalculatorV1`.  
  
## <a name="creating-the-pipeline-directory-structure"></a>Criando a estrutura de diretórios de Pipeline  
 O modelo de suplemento requer os assemblies de segmento de pipeline ser colocado em uma estrutura de diretório especificado. Para obter mais informações sobre a estrutura do pipeline, consulte [requisitos de desenvolvimento de Pipeline](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
#### <a name="to-create-the-pipeline-directory-structure"></a>Para criar a estrutura de diretório de pipeline  
  
1.  Crie uma pasta de aplicativo em qualquer lugar no seu computador.  
  
2.  Nessa pasta, crie a seguinte estrutura:  
  
    ```  
    Pipeline  
      AddIns  
        CalcV1  
        CalcV2  
      AddInSideAdapters  
      AddInViews  
      Contracts  
      HostSideAdapters  
    ```  
  
     Não é necessário colocar a estrutura de pastas do pipeline na sua pasta de aplicativo; Isso é feito aqui apenas para conveniência. A etapa apropriada, passo a passo explica como alterar o código se a estrutura de pastas do pipeline está em um local diferente. Consulte a discussão de requisitos de diretório do pipeline em [requisitos de desenvolvimento de Pipeline](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
    > [!NOTE]
    >  O `CalcV2` pasta não é usada neste passo a passo; é um espaço reservado para [passo a passo: Habilitando compatibilidade com versões anteriores, como alterações do seu Host](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848).  
  
## <a name="creating-the-contract-and-views"></a>Criar o contrato e modos de exibição  
 O segmento de contrato para este pipeline define o `ICalc1Contract` interface, que define quatro métodos: `add`, `subtract`, `multiply`, e `divide`.  
  
#### <a name="to-create-the-contract"></a>Para criar um contrato  
  
1.  Na solução do Visual Studio chamada `CalculatorV1`, abra o `Calc1Contract` projeto.  
  
2.  Em **Solution Explorer**, adicione referências para os seguintes assemblies para o `Calc1Contract` projeto:  
  
     System.AddIn.Contract.dll  
  
     System.AddIn.dll  
  
3.  Em **Solution Explorer**, excluir a classe padrão que é adicionada ao novo **biblioteca de classes** projetos.  
  
4.  Em **Solution Explorer**, adicionar um novo item ao projeto, usando o **Interface** modelo. No **Adicionar Novo Item** caixa de diálogo, o nome da interface `ICalc1Contract`.  
  
5.  No arquivo de interface, adicione referências a namespace <xref:System.AddIn.Contract> e <xref:System.AddIn.Pipeline>.  
  
6.  Use o código a seguir para concluir este segmento de contrato. Observe que esta interface deve ter o <xref:System.AddIn.Pipeline.AddInContractAttribute> atributo.  
  
     [!code-csharp[AddInP1Contract#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Contract/cs/ICalc1Contract.cs#1)]
     [!code-vb[AddInP1Contract#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Contract/vb/ICalc1Contract.vb#1)]  
  
7.  Opcionalmente, compile a solução do Visual Studio. A solução não pode ser executada até que o procedimento final, mas criá-lo depois de cada procedimento garante que cada projeto é corrigir.  
  
 Como o modo de exibição e o host do modo de exibição de suplemento geralmente têm o mesmo código, especialmente na primeira versão de um suplemento, você pode criar facilmente os modos de exibição ao mesmo tempo. Diferem por apenas um fator: requer o modo de exibição de <xref:System.AddIn.Pipeline.AddInBaseAttribute> atributo, enquanto o modo de host do suplemento não exige que todos os atributos.  
  
#### <a name="to-create-the-add-in-view"></a>Para criar o modo de exibição  
  
1.  Adicionar um novo projeto denominado `Calc1AddInView` para o `CalculatorV1` solução. Baseá-la no **biblioteca de classes** modelo.  
  
2.  Em **Solution Explorer**, adicione uma referência ao System.AddIn.dll para o `Calc1AddInView` projeto.  
  
3.  Em **Solution Explorer**, excluir a classe padrão que é adicionada ao novo **biblioteca de classes** projetos e adicionar um novo item ao projeto, usando o **Interface** modelo. No **Adicionar Novo Item** caixa de diálogo, o nome da interface `ICalculator`.  
  
4.  No arquivo de interface, adicione uma referência ao namespace para <xref:System.AddIn.Pipeline>.  
  
5.  Use o código a seguir para concluir este modo de exibição do suplemento. Observe que esta interface deve ter o <xref:System.AddIn.Pipeline.AddInBaseAttribute> atributo.  
  
     [!code-csharp[AddInP1AddInViews#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInViews/cs/Calc1AddInView.cs#1)]
     [!code-vb[AddInP1AddInViews#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInViews/vb/Calc1AddInView.vb#1)]  
  
6.  Opcionalmente, compile a solução do Visual Studio.  
  
#### <a name="to-create-the-host-view-of-the-add-in"></a>Para criar o modo de host do suplemento  
  
1.  Adicionar um novo projeto denominado `Calc1HVA` para o `CalculatorV1` solução. Baseá-la no **biblioteca de classes** modelo.  
  
2.  Em **Solution Explorer**, excluir a classe padrão que é adicionada ao novo **biblioteca de classes** projetos e adicionar um novo item ao projeto, usando o **Interface** modelo. No **Adicionar Novo Item** caixa de diálogo, o nome da interface `ICalculator`.  
  
3.  No arquivo de interface, use o código a seguir para concluir o modo de host do suplemento.  
  
     [!code-csharp[AddInP1HVA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HVA/cs/calc1hva.cs#1)]
     [!code-vb[AddInP1HVA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HVA/vb/Calc1HVA.vb#1)]  
  
4.  Opcionalmente, compile a solução do Visual Studio.  
  
## <a name="creating-the-add-in-side-adapter"></a>Criar o adaptador de adicionar no lado  
 Esse adaptador adicionar no lado consiste em um adaptador de exibição para o contrato. Este segmento de pipeline converte os tipos do modo de exibição para o contrato.  
  
 Nesse pipeline, o suplemento fornece um serviço para o host e os tipos de fluam do suplemento para o host. Porque nenhum tipo de fluxo do host para o suplemento, você não precisa incluem um adaptador de exibição de contrato no lado do suplemento deste pipeline.  
  
#### <a name="to-create-the-add-in-side-adapter"></a>Para criar o adaptador do lado do suplemento  
  
1.  Adicionar um novo projeto denominado `Calc1AddInSideAdapter` para o `CalculatorV1` solução. Baseá-la no **biblioteca de classes** modelo.  
  
2.  Em **Solution Explorer**, adicione referências para os seguintes assemblies para o `Calc1AddInSideAdapter` projeto:  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  Adicione referências de projeto para os projetos para os segmentos de pipeline adjacente:  
  
     `Calc1AddInView`  
  
     `Calc1Contract`  
  
4.  Selecione cada referência de projeto e, em **propriedades** definir **Copy Local** para **False**. No Visual Basic, utilize o **referências** guia de **propriedades do projeto** definir **Copy Local** para **False** para as duas referências de projeto.  
  
5.  Renomear a classe do projeto padrão `CalculatorViewToContractAddInSideAdapter`.  
  
6.  No arquivo de classe, adicione referências a namespace <xref:System.AddIn.Pipeline>.  
  
7.  No arquivo de classe, adicione referências de namespace para os segmentos adjacentes: `CalcAddInViews` e `CalculatorContracts`. (No Visual Basic, essas referências de namespace são `Calc1AddInView.CalcAddInViews` e `Calc1Contract.CalculatorContracts`, a menos que você tiver desativado os namespaces padrão em seus projetos do Visual Basic.)  
  
8.  Aplicar o <xref:System.AddIn.Pipeline.AddInAdapterAttribute> de atributo para o `CalculatorViewToContractAddInSideAdapter` classe para identificá-lo como o adaptador do lado do suplemento.  
  
9. Verifique o `CalculatorViewToContractAddInSideAdapter` herdar da classe <xref:System.AddIn.Pipeline.ContractBase>, que fornece uma implementação padrão da <xref:System.AddIn.Contract.IContract> de interface e implementa a interface de contrato para o pipeline, `ICalc1Contract`.  
  
10. Adicione um construtor público que aceita um `ICalculator`, armazena em cache em um campo particular e chama o construtor de classe base.  
  
11. Implemente os membros de `ICalc1Contract`, simplesmente chamar os membros correspondentes a `ICalculator` instância que é passada para o construtor e retorna os resultados. Isso se adapta o modo de exibição (`ICalculator`) para o contrato (`ICalc1Contract`).  
  
     O código a seguir mostra o adaptador de adicionar no lado concluído.  
  
     [!code-csharp[AddInP1AddInSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInSideAdapters/cs/Calc1ViewToContractAddInSideAdapter.cs#1)]
     [!code-vb[AddInP1AddInSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInSideAdapters/vb/Calc1ViewToContractAddInSideAdapter.vb#1)]  
  
12. Opcionalmente, compile a solução do Visual Studio.  
  
## <a name="creating-the-host-side-adapter"></a>Criar o adaptador do lado do Host  
 Esse adaptador do host consiste em um adaptador de exibição de contrato. Este segmento adapta o contrato para o modo de host do suplemento.  
  
 Nesse pipeline, o suplemento fornece um serviço para o host e o fluxo de tipos do suplemento para o host. Porque nenhum tipo de fluxo do host para o suplemento, você não precisa incluem um adaptador de exibição para o contrato.  
  
 Para implementar o gerenciamento de vida útil, use um <xref:System.AddIn.Pipeline.ContractHandle> objeto para anexar um token de tempo de vida para o contrato. Você deve manter uma referência a esse identificador em ordem para gerenciamento de vida útil trabalhar. Depois que o token é aplicado, sem programação adicional é necessária porque o sistema suplemento pode descartar objetos quando eles não estão sendo usados e disponibilizá-las para coleta de lixo. Para obter mais informações, consulte [gerenciamento de vida útil](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).  
  
#### <a name="to-create-the-host-side-adapter"></a>Para criar o adaptador do host  
  
1.  Adicionar um novo projeto denominado `Calc1HostSideAdapter` para o `CalculatorV1` solução. Baseá-la no **biblioteca de classes** modelo.  
  
2.  Em **Solution Explorer**, adicione referências para os seguintes assemblies para o `Calc1HostSideAdapter` projeto:  
  
     System.AddIn.dll  
  
     System.AddIn.Contract.dll  
  
3.  Adicione referências de projeto para os projetos para os segmentos adjacentes:  
  
     `Calc1Contract`  
  
     `Calc1HVA`  
  
4.  Selecione cada referência de projeto e, em **propriedades** definir **Copy Local** para **False**. No Visual Basic, utilize o **referências** guia de **propriedades do projeto** definir **Copy Local** para **False** para as duas referências de projeto.  
  
5.  Renomear a classe do projeto padrão `CalculatorContractToViewHostSideAdapter`.  
  
6.  No arquivo de classe, adicione referências a namespace <xref:System.AddIn.Pipeline>.  
  
7.  No arquivo de classe, adicione referências de namespace para os segmentos adjacentes: `CalcHVAs` e `CalculatorContracts`. (No Visual Basic, essas referências de namespace são `Calc1HVA.CalcHVAs` e `Calc1Contract.CalculatorContracts`, a menos que você tiver desativado os namespaces padrão em seus projetos do Visual Basic.)  
  
8.  Aplicar o <xref:System.AddIn.Pipeline.HostAdapterAttribute> de atributo para o `CalculatorContractToViewHostSideAdapter` classe para identificá-lo como o segmento de adaptador do host.  
  
9. Verifique o `CalculatorContractToViewHostSideAdapter` classe implementa a interface que representa o modo de host do suplemento: `Calc1HVAs.ICalculator` (`Calc1HVA.CalcHVAs.ICalculator` no Visual Basic).  
  
10. Adicione um construtor público que aceita o tipo de contrato de pipeline, `ICalc1Contract`. O construtor deve armazenar em cache a referência ao contrato. Ele também deve criar e armazenar em cache um novo <xref:System.AddIn.Pipeline.ContractHandle> para o contrato, para gerenciar o tempo de vida do suplemento.  
  
    > [!IMPORTANT]
    >  O <xref:System.AddIn.Pipeline.ContractHandle> é fundamental para o gerenciamento de vida útil. Se você não conseguir manter uma referência para o <xref:System.AddIn.Pipeline.ContractHandle> de objetos, coleta de lixo recuperará e o pipeline será desligada quando o programa não espera. Isso pode levar a erros que são difíceis de diagnosticar, como <xref:System.AppDomainUnloadedException>. Desligamento é um estágio normal na vida de um pipeline, portanto não é possível para o código de tempo de vida de gerenciamento detectar essa condição é um erro.  
  
11. Implemente os membros de `ICalculator`, simplesmente chamar os membros correspondentes a `ICalc1Contract` instância que é passada para o construtor e retorna os resultados. Isso se adapta o contrato (`ICalc1Contract`) para o modo de exibição (`ICalculator`).  
  
     O código a seguir mostra o adaptador do lado do host concluído.  
  
     [!code-csharp[AddInP1HostSideAdapters#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1HostSideAdapters/cs/Calc1ContractToViewHostSideAdapter.cs#1)]
     [!code-vb[AddInP1HostSideAdapters#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1HostSideAdapters/vb/Calc1ContractToViewHostSideAdapter.vb#1)]  
  
12. Opcionalmente, compile a solução do Visual Studio.  
  
## <a name="creating-the-host"></a>Criando o Host  
 Um aplicativo host interage com o suplemento por meio da exibição de host do suplemento. Ele usa o suplemento detecção e ativação métodos fornecidos pelo <xref:System.AddIn.Hosting.AddInStore> e <xref:System.AddIn.Hosting.AddInToken> classes para fazer o seguinte:  
  
-   Atualize o cache de informações de pipeline e o suplemento.  
  
-   Localizar suplementos do tipo de exibição de host, `ICalculator`, sob o diretório raiz do pipeline especificado.  
  
-   Solicite ao usuário para especificar qual suplemento para usar.  
  
-   Ative o suplemento selecionado em um novo domínio de aplicativo com um nível de confiança de segurança especificados.  
  
-   Executar personalizado `RunCalculator` método, que chama os métodos do suplemento conforme especificado pelo modo de host do suplemento.  
  
#### <a name="to-create-the-host"></a>Para criar o host  
  
1.  Adicionar um novo projeto denominado `Calc1Host` para o `CalculatorV1` solução. Baseá-la no **aplicativo de Console** modelo.  
  
2.  Em **Solution Explorer**, adicione uma referência ao assembly System.AddIn.dll para o `Calc1Host` projeto.  
  
3.  Adicione uma referência de projeto para o `Calc1HVA` projeto. Selecione a referência de projeto e na **propriedades** definir **Copy Local** para **False**. No Visual Basic, utilize o **referências** guia de **propriedades do projeto** definir **Copy Local** para **False**.  
  
4.  Renomeie o arquivo de classe (módulo no Visual Basic) `MathHost1`.  
  
5.  No Visual Basic, use o **aplicativo** guia o **propriedades do projeto** caixa de diálogo para definir **objeto de inicialização** para **Sub Main**.  
  
6.  No arquivo de classe ou módulo, adicione uma referência ao namespace para <xref:System.AddIn.Hosting>.  
  
7.  No arquivo de classe ou módulo, adicione uma referência de namespace para o modo de host do suplemento: `CalcHVAs`. (No Visual Basic, essa referência de namespace é `Calc1HVA.CalcHVAs`, a menos que você tiver desativado os namespaces padrão em seus projetos do Visual Basic.)  
  
8.  No **Solution Explorer**, selecione a solução e o **projeto** menu escolha **propriedades**. No **páginas de propriedade da solução** caixa de diálogo, defina o **único projeto de inicialização** ser este projeto de aplicativo de host.  
  
9. No arquivo de classe ou módulo, use o <xref:System.AddIn.Hosting.AddInStore.Update%2A?displayProperty=nameWithType> método para atualizar o cache. Use o <xref:System.AddIn.Hosting.AddInStore.FindAddIn%2A?displayProperty=nameWithType> método para obter uma coleção de tokens e use o <xref:System.AddIn.Hosting.AddInToken.Activate%2A?displayProperty=nameWithType> método para ativar um suplemento.  
  
     O código a seguir mostra o aplicativo de host completo.  
  
     [!code-csharp[AddInP1Host#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1Host/cs/MathHost1.cs#1)]
     [!code-vb[AddInP1Host#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1Host/vb/MathHost1.vb#1)]  
  
    > [!NOTE]
    >  Esse código supõe que a estrutura de pastas do pipeline está localizada na pasta do aplicativo. Se você localizá-lo em outro local, altere a linha de código que define o `addInRoot` variável, para que a variável contém o caminho para a estrutura de diretório do pipeline.  
  
     O código usa um `ChooseCalculator` método para listar os tokens e solicitar ao usuário para escolher um suplemento. O `RunCalculator` método solicita ao usuário para expressões de cálculos matemáticos simples, analisa as expressões que usam o `Parser` classe e exibe os resultados retornados pelo suplemento.  
  
10. Opcionalmente, compile a solução do Visual Studio.  
  
## <a name="creating-the-add-in"></a>Criando o suplemento  
 Um suplemento implementa os métodos especificados, o modo de exibição. Esse suplemento implementa o `Add`, `Subtract`, `Multiply`, e `Divide` operações e retorna os resultados para o host.  
  
#### <a name="to-create-the-add-in"></a>Para criar o suplemento  
  
1.  Adicionar um novo projeto denominado `AddInCalcV1` para o `CalculatorV1` solução. Baseá-la no **biblioteca de classes** modelo.  
  
2.  Em **Solution Explorer**, adicione uma referência ao assembly System.AddIn.dll ao projeto.  
  
3.  Adicione uma referência de projeto para o `Calc1AddInView` projeto. Selecione a referência de projeto e na **propriedades**, defina **Copy Local** para **False**. No Visual Basic, utilize o **referências** guia de **propriedades do projeto** definir **Copy Local** para **False** para a referência de projeto.  
  
4.  Renomeie a classe `AddInCalcV1`.  
  
5.  No arquivo de classe, adicione uma referência ao namespace para <xref:System.AddIn> e o segmento de exibição: `CalcAddInViews` (`Calc1AddInView.CalcAddInViews` no Visual Basic).  
  
6.  Aplicar o <xref:System.AddIn.AddInAttribute> de atributo para o `AddInCalcV1` classe para identificar a classe como um suplemento.  
  
7.  Verifique o `AddInCalcV1` classe implementa a interface que representa o modo de exibição: `CalcAddInViews.ICalculator` (`Calc1AddInView.CalcAddInViews.ICalculator` no Visual Basic).  
  
8.  Implemente os membros das `ICalculator` retornando os resultados dos cálculos apropriados.  
  
     O código a seguir mostra o suplemento concluído.  
  
     [!code-csharp[AddInP1AddInCalcV1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AddInP1AddInCalcV1/cs/AddInCalcV1.cs#1)]
     [!code-vb[AddInP1AddInCalcV1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AddInP1AddInCalcV1/vb/AddInCalcV1.vb#1)]  
  
9. Opcionalmente, compile a solução do Visual Studio.  
  
## <a name="deploying-the-pipeline"></a>Implantando o Pipeline  
 Agora você está pronto para criar e implantar os segmentos de adicionar a estrutura do diretório pipeline necessários.  
  
#### <a name="to-deploy-the-segments-to-the-pipeline"></a>Para implantar os segmentos de pipeline  
  
1.  Para cada projeto na solução, use o **criar** guia de **propriedades do projeto** (o **compilar** guia no Visual Basic) para definir o valor da **caminho de saída**  (o **caminho de saída de compilação** no Visual Basic). Se você nomeou sua pasta de aplicativo `MyApp`, por exemplo, seus projetos compilaria nas seguintes pastas:  
  
    |Projeto|Caminho|  
    |-------------|----------|  
    |AddInCalcV1|MyApp\Pipeline\AddIns\CalcV1|  
    |Calc1AddInSideAdapter|MyApp\Pipeline\AddInSideAdapters|  
    |Calc1AddInView|MyApp\Pipeline\AddInViews|  
    |Calc1Contract|MyApp\Pipeline\Contracts|  
    |Calc1Host|MyApp|  
    |Calc1HostSideAdapter|MyApp\Pipeline\HostSideAdapters|  
    |Calc1HVA|MyApp|  
  
    > [!NOTE]
    >  Se você decidiu colocar sua estrutura de pasta de pipeline em um local diferente da pasta de seu aplicativo, você deve modificar os caminhos mostrados na tabela adequadamente. Consulte a discussão de requisitos de diretório do pipeline em [requisitos de desenvolvimento de Pipeline](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
2.  Compile a solução do Visual Studio.  
  
3.  Verifique os diretórios de pipeline e de aplicativo para garantir que os assemblies foram copiados para os diretórios corretos e que não há cópias extras dos assemblies foram instaladas nas pastas erradas.  
  
    > [!NOTE]
    >  Se você não alterou **Copy Local** para **False** para o `Calc1AddInView` projeto de referência no `AddInCalcV1` projeto, problemas de contexto do carregador impede que o suplemento que está sendo localizado.  
  
     Para obter informações sobre como implantar o pipeline, consulte [requisitos de desenvolvimento de Pipeline](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
## <a name="running-the-host-application"></a>Executando o aplicativo de Host  
 Agora você está pronto para executar o host e interagir com o suplemento.  
  
#### <a name="to-run-the-host-application"></a>Para executar o aplicativo de host  
  
1.  No prompt de comando, vá para o diretório de aplicativo e executar o aplicativo de host, `Calc1Host.exe`.  
  
2.  O host localiza todos os suplementos disponíveis do seu tipo e solicita que você selecione um suplemento. Digite **1** para o suplemento somente disponível.  
  
3.  Insira uma equação para o cálculo, como **2 + 2**. Deve haver espaços entre os números e o operador.  
  
4.  Tipo **sair** e pressione a **Enter** tecla para fechar o aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Habilitando a compatibilidade com versões anteriores, como as alterações de Host](http://msdn.microsoft.com/en-us/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
 [Passo a passo: Passando coleções entre Hosts e suplementos](http://msdn.microsoft.com/en-us/b532c604-548e-4fab-b11c-377257dd0ee5)  
 [Requisitos de desenvolvimento de pipeline](http://msdn.microsoft.com/en-us/ef9fa986-e80b-43e1-868b-247f4c1d9da5)  
 [Contratos, exibições e adaptadores](http://msdn.microsoft.com/en-us/a6460173-9507-4b87-8c07-d4ee245d715c)  
 [Desenvolvimento de pipeline](../../../docs/framework/add-ins/pipeline-development.md)
