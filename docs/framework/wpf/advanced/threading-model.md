---
title: Modelo de threading
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text on buttons [WPF], updating
- message processing [WPF], nested
- blocking operations [WPF]
- Common Language Runtime (CLR), locking mechanism
- locking mechanism of Common Language Runtime (CLR)
- threading model [WPF]
- Word [WPF], spelling checking
- button text [WPF], updating
- spelling checking in Word [WPF]
- asynchronous behavior [WPF], exposing
- nested message processing [WPF]
- reentrancy [WPF]
ms.assetid: 02d8fd00-8d7c-4604-874c-58e40786770b
ms.openlocfilehash: ef25123ed53ecf3e03e4f4c969bed2ef570591ad
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459033"
---
# <a name="threading-model"></a>Modelo de threading
O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] foi projetado para livrar os desenvolvedores das dificuldades de threading. Como resultado, a maioria dos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] desenvolvedores não precisará escrever uma interface que use mais de um thread. Como os programas multi-threaded são complexos e difíceis de serem depurados, deve-se evitá-los quando existem soluções single-threaded.  
  
 No entanto, não importa quão bem projetado, nenhuma estrutura de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] será capaz de fornecer uma solução de thread único para cada tipo de problema. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vem perto, mas ainda há situações em que vários threads melhoram [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] a capacidade de resposta ou o desempenho do aplicativo. Depois de abordar alguns documentos de suporte, este artigo explora algumas dessas situações e, em seguida, termina com uma discussão de alguns detalhes de nível mais baixo.  

> [!NOTE]
> Este tópico discute o threading usando o método <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> para chamadas assíncronas. Você também pode fazer chamadas assíncronas chamando o método <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, que pega um <xref:System.Action> ou <xref:System.Func%601> como um parâmetro.  O método <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> retorna um <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>, que tem uma propriedade <xref:System.Windows.Threading.DispatcherOperation.Task%2A>. Você pode usar a palavra-chave `await` com o <xref:System.Windows.Threading.DispatcherOperation> ou o <xref:System.Threading.Tasks.Task>associado. Se você precisar esperar de forma síncrona o <xref:System.Threading.Tasks.Task> retornado por um <xref:System.Windows.Threading.DispatcherOperation> ou <xref:System.Windows.Threading.DispatcherOperation%601>, chame o método de extensão <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A>.  Chamar <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> resultará em um deadlock. Para obter mais informações sobre como usar um <xref:System.Threading.Tasks.Task> para executar operações assíncronas, consulte paralelismo de tarefas.  O método <xref:System.Windows.Threading.Dispatcher.Invoke%2A> também tem sobrecargas que usam um <xref:System.Action> ou <xref:System.Func%601> como um parâmetro.  Você pode usar o método <xref:System.Windows.Threading.Dispatcher.Invoke%2A> para fazer chamadas síncronas passando um delegado, <xref:System.Action> ou <xref:System.Func%601>.  
  
<a name="threading_overview"></a>   
## <a name="overview-and-the-dispatcher"></a>Visão geral e o dispatcher  
 Normalmente, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos começam com dois threads: um para lidar com a renderização e outro para gerenciar o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. O thread de renderização é executado de forma efetiva em segundo plano enquanto o thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] recebe entrada, manipula eventos, pinta a tela e executa o código do aplicativo. A maioria dos aplicativos usa um único thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], embora em algumas situações seja melhor usar vários. Abordaremos isso com um exemplo posteriormente.  
  
 O [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de filas de threads de itens de trabalho dentro de um objeto chamado de <xref:System.Windows.Threading.Dispatcher>. O <xref:System.Windows.Threading.Dispatcher> seleciona itens de trabalho de acordo com a prioridade e executa cada um deles para conclusão.  Cada thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] deve ter pelo menos um <xref:System.Windows.Threading.Dispatcher>, e cada <xref:System.Windows.Threading.Dispatcher> pode executar itens de trabalho em exatamente um thread.  
  
 O truque para a criação de aplicativos responsivos e amigáveis é maximizar a taxa de transferência de <xref:System.Windows.Threading.Dispatcher> mantendo os itens de trabalho pequenos. Dessa forma, os itens nunca ficam obsoletos na fila de <xref:System.Windows.Threading.Dispatcher> aguardando o processamento. Qualquer atraso perceptível entre a entrada e a resposta pode frustrar um usuário.  
  
 Como [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplicativos devem lidar com operações grandes? E se o código envolver um cálculo grande ou precisar consultar um banco de dados em algum servidor remoto? Normalmente, a resposta é manipular a operação grande em um thread separado, deixando o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread livre para tendem a itens na fila de <xref:System.Windows.Threading.Dispatcher>. Quando a operação grande for concluída, ela poderá relatar seu resultado para o thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para exibição.  
  
 Historicamente, o Windows permite que [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementos sejam acessados somente pelo thread que os criou. Isso significa que um thread de segundo plano responsável por uma tarefa de execução longa não pode atualizar uma caixa de texto quando ele é concluído. O Windows faz isso para garantir a integridade dos componentes de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Uma caixa de listagem poderá ter uma aparência estranha se seu conteúdo for atualizado por um thread de segundo plano durante a pintura.  
  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tem um mecanismo de exclusão mútua interno que garante essa coordenação. A maioria das classes no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] deriva de <xref:System.Windows.Threading.DispatcherObject>. Na construção, um <xref:System.Windows.Threading.DispatcherObject> armazena uma referência ao <xref:System.Windows.Threading.Dispatcher> vinculado ao thread em execução no momento. Na verdade, o <xref:System.Windows.Threading.DispatcherObject> associa o thread que o cria. Durante a execução do programa, um <xref:System.Windows.Threading.DispatcherObject> pode chamar seu método público <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> examina a <xref:System.Windows.Threading.Dispatcher> associada ao thread atual e a compara com a referência <xref:System.Windows.Threading.Dispatcher> armazenada durante a construção. Se eles não corresponderem, <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> lançará uma exceção. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> deve ser chamado no início de cada método que pertence a um <xref:System.Windows.Threading.DispatcherObject>.  
  
 Se apenas um thread puder modificar o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], como threads em segundo plano interagem com o usuário? Um thread em segundo plano pode pedir ao thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] para executar uma operação em seu nome. Ele faz isso registrando um item de trabalho com a <xref:System.Windows.Threading.Dispatcher> do thread [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. A classe <xref:System.Windows.Threading.Dispatcher> fornece dois métodos para registrar itens de trabalho: <xref:System.Windows.Threading.Dispatcher.Invoke%2A> e <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>. Ambos os métodos agendam um delegado para execução. <xref:System.Windows.Threading.Dispatcher.Invoke%2A> é uma chamada síncrona – ou seja, não retorna até que o thread [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] realmente termine de executar o delegado. <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> é assíncrona e retorna imediatamente.  
  
 O <xref:System.Windows.Threading.Dispatcher> ordena os elementos em sua fila por prioridade. Há dez níveis que podem ser especificados ao adicionar um elemento à fila de <xref:System.Windows.Threading.Dispatcher>. Essas prioridades são mantidas na enumeração de <xref:System.Windows.Threading.DispatcherPriority>. Informações detalhadas sobre os níveis de <xref:System.Windows.Threading.DispatcherPriority> podem ser encontradas na documentação do [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].  
  
<a name="samples"></a>   
## <a name="threads-in-action-the-samples"></a>Threads em ação: as amostras  
  
<a name="prime_number"></a>   
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>Um aplicativo single-threaded com um cálculo de execução longa  
 A maioria das GUIs (interfaces gráficas do usuário) passam uma grande parte do tempo ocioso enquanto aguarda eventos gerados em resposta às interações do usuário. Com a programação cuidadosa, esse tempo ocioso pode ser usado crítica, sem afetar a capacidade de resposta do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. O modelo de Threading [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] não permite que a entrada interrompa uma operação que ocorre no thread [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Isso significa que você deve se certificar de retornar ao <xref:System.Windows.Threading.Dispatcher> periodicamente para processar eventos de entrada pendentes antes que eles fiquem obsoletos.  
  
 Considere o exemplo a seguir:  
  
 ![Captura de tela que mostra o encadeamento de números primos.](./media/threading-model/threading-prime-numbers.png)  
  
 Este aplicativo simples faz uma contagem ascendente a partir do três, pesquisando os números primos. Quando o usuário clica no botão **Iniciar** , a pesquisa começa. Quando o programa encontra um primo, ele atualiza a interface do usuário com sua descoberta. A qualquer momento, o usuário pode parar a pesquisa.  
  
 Embora seja simples o suficiente, a pesquisa de números primos poderá continuar para sempre, o que apresenta algumas dificuldades.  Se tratarmos toda a pesquisa dentro do manipulador de eventos de clique do botão, nunca daremos à [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] thread a oportunidade de lidar com outros eventos. O [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] não seria capaz de responder a entradas ou processar mensagens. Ele nunca redesenhará e nunca responderá aos cliques do botão.  
  
 Poderíamos realizar a pesquisa de números primos em um thread separado, mas precisaríamos lidar com problemas de sincronização. Com uma abordagem single-threaded, podemos atualizar diretamente o rótulo que lista o maior primo encontrado.  
  
 Se dividirmos a tarefa de cálculo em partes gerenciáveis, poderemos retornar periodicamente ao <xref:System.Windows.Threading.Dispatcher> e processar eventos. Podemos dar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uma oportunidade de redesenhar e processar a entrada.  
  
 A melhor maneira de dividir o tempo de processamento entre o cálculo e a manipulação de eventos é gerenciar o cálculo do <xref:System.Windows.Threading.Dispatcher>. Usando o método <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>, podemos agendar verificações de números primos na mesma fila da qual [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] eventos são extraídos. Em nosso exemplo, agendamos somente uma única verificação de números primos por vez. Depois que a verificação de números primos for concluída, agendaremos a próxima verificação imediatamente. Essa verificação prossegue somente após os eventos de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pendentes terem sido tratados.  
  
 ![Captura de tela que mostra a fila do Dispatcher.](./media/threading-model/threading-dispatcher-queue.png)  
  
 O Microsoft Word realiza a verificação ortográfica usando esse mecanismo. A verificação ortográfica é feita em segundo plano usando o tempo ocioso do thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Vamos dar uma olhada no código.  
  
 O exemplo a seguir mostra o XAML que cria a interface do usuário.  
  
 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]  
  
 O exemplo a seguir mostra o code-behind.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]  
  
 O exemplo a seguir mostra o manipulador de eventos para o <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]  
  
 Além de atualizar o texto na <xref:System.Windows.Controls.Button>, esse manipulador é responsável por agendar a primeira verificação de número primo adicionando um delegado à fila de <xref:System.Windows.Threading.Dispatcher>. Um pouco depois que esse manipulador de eventos concluiu seu trabalho, o <xref:System.Windows.Threading.Dispatcher> selecionará esse delegado para execução.  
  
 Como mencionamos anteriormente, <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> é o membro <xref:System.Windows.Threading.Dispatcher> usado para agendar um delegado para execução. Nesse caso, escolhemos a prioridade de <xref:System.Windows.Threading.DispatcherPriority.SystemIdle>. O <xref:System.Windows.Threading.Dispatcher> executará esse delegado somente quando não houver eventos importantes a serem processados. A capacidade de resposta da [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] é mais importante do que a verificação de números. Também passamos um novo delegado que representa a rotina de verificação de números.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]  
  
 Esse método verifica se o próximo número ímpar é um primo. Se for primo, o método atualizará diretamente o `bigPrime`<xref:System.Windows.Controls.TextBlock> para refletir sua descoberta. Podemos fazer isso porque o cálculo é feito no mesmo thread que foi usado para criar o componente. Optamos por usar um thread separado para o cálculo, teríamos que usar um mecanismo de sincronização mais complicado e executar a atualização no thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Demonstraremos essa situação a seguir.  
  
 Para obter o código-fonte completo deste exemplo, consulte o [aplicativo de thread único com exemplo de cálculo de longa execução](https://go.microsoft.com/fwlink/?LinkID=160038)  
  
<a name="weather_sim"></a>   
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>Manipulando uma operação de bloqueio com um thread de segundo plano  
 A manipulação de operações de bloqueio em um aplicativo gráfico pode ser difícil. Não desejamos chamar métodos de bloqueio por meio de manipuladores de eventos, pois o aplicativo parecerá congelado. Podemos usar um thread separado para lidar com essas operações, mas quando terminarmos, temos que sincronizar com o thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] porque não podemos modificar diretamente a GUI de nosso thread de trabalho. Podemos usar <xref:System.Windows.Threading.Dispatcher.Invoke%2A> ou <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> para inserir delegados no <xref:System.Windows.Threading.Dispatcher> do thread [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Eventualmente, esses delegados serão executados com permissão para modificar elementos de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 Neste exemplo, simulamos uma chamada de procedimento remoto que recupera uma previsão do tempo. Usamos um thread de trabalho separado para executar essa chamada e agendamos um método Update na <xref:System.Windows.Threading.Dispatcher> do thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] quando terminarmos.  
  
 ![Captura de tela que mostra a interface do usuário do clima.](./media/threading-model/threading-weather-ui.png)  
  
 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]  
  
 Veja a seguir alguns dos detalhes a serem observados.  
  
- Criando o manipulador de botões  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]  
  
 Quando o botão recebe um clique, exibimos o desenho do relógio e iniciamos sua animação. Desabilitamos o botão. Invocamos o método `FetchWeatherFromServer` em um novo thread e, em seguida, retornamos, permitindo que o <xref:System.Windows.Threading.Dispatcher> processe eventos enquanto aguardamos para coletar a previsão do tempo.  
  
- Buscando o clima  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]  
  
 Para manter as coisas simples, na verdade, não apresentamos nenhum código de rede neste exemplo. Em vez disso, simulamos o atraso do acesso à rede colocando nosso novo thread em suspensão por quatro segundos. Neste momento, o thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] original ainda está em execução e respondendo a eventos. Para mostrar isso, deixamos uma animação em execução e os botões Minimizar e Maximizar também continuam funcionando.  
  
 Quando o atraso é concluído e selecionamos aleatoriamente nossa previsão do tempo, é hora de relatar de volta para o thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Fazemos isso agendando uma chamada para `UpdateUserInterface` no thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] usando a <xref:System.Windows.Threading.Dispatcher>desse thread. Passamos uma cadeia de caracteres que descreve o clima para essa chamada de método agendada.  
  
- Atualizando o [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]  
  
 Quando o <xref:System.Windows.Threading.Dispatcher> no thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] tem tempo, ele executa a chamada agendada para `UpdateUserInterface`. Esse método para a animação do relógio e escolhe uma imagem para descrever o clima. Ele exibe essa imagem e restaura o botão “Buscar Previsão”.  
  
<a name="multi_browser"></a>   
### <a name="multiple-windows-multiple-threads"></a>Várias janelas, vários threads  
 Alguns aplicativos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] exigem várias janelas de nível superior. É perfeitamente aceitável que uma combinação de thread/<xref:System.Windows.Threading.Dispatcher> gerencie várias janelas, mas às vezes vários threads realizam um trabalho melhor. Isso será especialmente verdadeiro se houver uma possibilidade de que uma das janelas monopolize o thread.  
  
 O Windows Explorer funciona dessa maneira. Cada nova janela do Explorer pertence ao processo original, mas é criada sob o controle de um thread independente.  
  
 Usando um controle de <xref:System.Windows.Controls.Frame> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], podemos exibir páginas da Web. Podemos criar facilmente um substituto simples do Internet Explorer. Começamos com um recurso importante: a capacidade de abrir uma nova janela do Explorer. Quando o usuário clica no botão “Nova Janela”, iniciamos uma cópia de nossa janela em um thread separado. Dessa forma, operações de execução longa ou de bloqueio em uma das janelas não bloquearão todas as outras janelas.  
  
 Na realidade, o modelo de navegador da Web tem seu próprio modelo de threading complicado. Nós o escolhemos porque deve ser conhecido pela maioria dos leitores.  
  
 O exemplo a seguir mostra o código.  
  
 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]  
  
 Os seguintes segmentos de threading desse código são os mais interessantes para nós neste contexto:  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]  
  
 Esse método é chamado quando o botão “Nova Janela” recebe um clique. Ele cria um novo thread e o inicia de forma assíncrona.  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]  
  
 Esse método é o ponto de partida para o novo thread. Criamos uma nova janela sob o controle desse thread. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cria automaticamente uma nova <xref:System.Windows.Threading.Dispatcher> para gerenciar o novo thread. Tudo o que temos a fazer para tornar a janela funcional é iniciar o <xref:System.Windows.Threading.Dispatcher>.  
  
<a name="stumbling_points"></a>   
## <a name="technical-details-and-stumbling-points"></a>Detalhes técnicos e obstáculos  
  
### <a name="writing-components-using-threading"></a>Escrevendo componentes usando o threading  
 O guia do desenvolvedor do Microsoft .NET Framework descreve um padrão de como um componente pode expor o comportamento assíncrono para seus clientes (consulte [visão geral do padrão assíncrono baseado em evento](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)). Por exemplo, suponha que queríamos empacotar o método `FetchWeatherFromServer` em um componente reutilizável e não-gráfico. Seguindo o padrão do Standard Microsoft .NET Framework, isso seria semelhante ao seguinte.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]  
  
 O `GetWeatherAsync` usaria uma das técnicas descritas anteriormente, como a criação de um thread de segundo plano, para fazer o trabalho de forma assíncrona, não bloqueando o thread de chamada.  
  
 Uma das partes mais importantes desse padrão é chamar o método *methodname*`Completed` no mesmo thread que chamou o método *MethodName*`Async` para começar. Você pode fazer isso usando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] razoavelmente fácil, armazenando <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>— mas o componente não-gráfico só poderia ser usado em aplicativos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], não em [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou em programas ASP.NET.  
  
 A classe <xref:System.Windows.Threading.DispatcherSynchronizationContext> lida com essa necessidade — imagine-a como uma versão simplificada do <xref:System.Windows.Threading.Dispatcher> que funciona com outras estruturas de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] também.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]  
  
### <a name="nested-pumping"></a>Bombeamento aninhado  
 Às vezes, não é viável bloquear completamente o thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Vamos considerar o método <xref:System.Windows.MessageBox.Show%2A> da classe <xref:System.Windows.MessageBox>. <xref:System.Windows.MessageBox.Show%2A> não retorna até que o usuário clique no botão OK. No entanto, ele cria uma janela que deve ter um loop de mensagens para ser interativa. Enquanto aguardamos até que o usuário clique em OK, a janela do aplicativo original não responde à entrada do usuário. No entanto, ele continua processando mensagens de pintura. A janela original se redesenha quando é coberta e revelada.  
  
 ![Captura de tela que mostra uma MessageBox com um botão OK](./media/threading-model/threading-message-loop.png)  
  
 Algum thread deve ser responsável pela janela da caixa de mensagem. O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poderá criar um novo thread apenas para a janela da caixa de mensagem, mas esse thread não poderá pintar os elementos desabilitados na janela original (lembre-se da discussão anterior sobre exclusão mútua). Em vez disso, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] usa um sistema de processamento de mensagens aninhado. A classe <xref:System.Windows.Threading.Dispatcher> inclui um método especial chamado <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>, que armazena o ponto de execução atual de um aplicativo e, em seguida, inicia um novo loop de mensagem. Quando o loop de mensagem aninhado é concluído, a execução é retomada após a chamada de <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> original.  
  
 Nesse caso, <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> mantém o contexto do programa na chamada para <xref:System.Windows.MessageBox>.<xref:System.Windows.MessageBox.Show%2A>, e ele inicia um novo loop de mensagem para redesenhar a janela de plano de fundo e manipular a entrada para a janela da caixa de mensagem. Quando o usuário clica em OK e limpa a janela pop-up, o loop aninhado é encerrado e o controle é retomado após a chamada para <xref:System.Windows.MessageBox.Show%2A>.  
  
### <a name="stale-routed-events"></a>Eventos roteados obsoletos  
 O sistema de eventos roteados no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] notifica árvores inteiras quando os eventos são gerados.  
  
 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]  
  
 Quando o botão esquerdo do mouse é pressionado sobre a elipse, `handler2` é executado. Após a conclusão do `handler2`, o evento é passado ao objeto <xref:System.Windows.Controls.Canvas>, que usa `handler1` para processá-lo. Isso ocorrerá somente se `handler2` não marcar explicitamente o objeto de evento como manipulado.  
  
 É possível que `handler2` levará muito tempo processando esse evento. `handler2` pode usar <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> para iniciar um loop de mensagem aninhado que não retorna por horas. Se `handler2` não marcar o evento como manipulado quando esse loop de mensagem for concluído, o evento será passado para a árvore, embora seja muito antigo.  
  
### <a name="reentrancy-and-locking"></a>Reentrada e bloqueio  
 O mecanismo de bloqueio do Common Language Runtime (CLR) não se comporta exatamente como alguém pode imaginar; uma delas pode esperar que um thread interrompa completamente a operação ao solicitar um bloqueio. Na realidade, o thread continua recebendo e processando mensagens de alta prioridade. Isso ajuda a impedir bloqueios e torna a interface minimamente dinâmica, mas introduz a possibilidade de bugs sutis.  A grande maioria do tempo que você não precisa saber nada a respeito disso, mas em circunstâncias raras (geralmente envolvendo [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] mensagens de janela ou componentes COM STA), vale a pena saber.  
  
 A maioria das interfaces não é criada com a segurança de thread em mente porque os desenvolvedores trabalham sob a suposição de que um [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nunca é acessado por mais de um thread. Nesse caso, esse único thread pode fazer alterações ambientais em tempos inesperados, causando os efeitos indesejados que o <xref:System.Windows.Threading.DispatcherObject> mecanismo de exclusão mútua deve resolver. Considere o seguinte pseudocódigo:  
  
 ![Diagrama que mostra a reentrância de Threading.](./media/threading-model/threading-reentrancy.png "ThreadingReentrancy")  
  
 Na maioria das vezes, essa é a coisa certa, mas há ocasiões em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] em que essa reentrância inesperada pode realmente causar problemas. Portanto, em determinados momentos chave, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chama <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>, que altera a instrução de bloqueio desse thread para usar o bloqueio de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] livre de reentrada, em vez do bloqueio CLR comum.  
  
 Então, por que a equipe do CLR escolheu esse comportamento? Isso tinha a ver com objetos COM STA e com o thread de finalização. Quando um objeto é coletado pelo lixo, seu método de `Finalize` é executado no thread do finalizador dedicado, não no thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. E aí está o problema, porque um objeto COM STA criado no thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] só pode ser descartado no thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. O CLR faz o equivalente de um <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (nesse caso, usando Win32's `SendMessage`). Mas se o thread de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] estiver ocupado, o thread do finalizador será interrompido e o objeto COM STA não poderá ser descartado, o que criará um sério vazamento de memória. Portanto, a equipe do CLR fez a chamada difícil para que os bloqueios funcionem da maneira que fazem.  
  
 A tarefa para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é evitar a reentrância inesperada sem reintroduzir o vazamento de memória, motivo pelo qual não bloqueamos a reentrância em todos os lugares.  
  
## <a name="see-also"></a>Consulte também

- [Amostra de aplicativo single-threaded com um cálculo de execução longa](https://go.microsoft.com/fwlink/?LinkID=160038)
