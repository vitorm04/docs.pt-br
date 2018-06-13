---
title: Criando a classe GamePiece
ms.date: 03/30/2017
ms.assetid: 37a27a86-ac1c-47be-b477-cb4b819459d3
ms.openlocfilehash: 0939da6eca579bd030bfe18b24d8364fbcc4fc82
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744506"
---
# <a name="creating-the-gamepiece-class"></a>Criando a classe GamePiece
A classe **GamePiece** encapsula toda a funcionalidade necessária para carregar uma imagem de uma peça do jogo da Microsoft XNA, controlar o estado do mouse em relação à peça do jogo, capturar o mouse, fornecer processamento de inércia e manipulação e fornecer a capacidade de pulo quando a peça do jogo atingir os limites da porta de exibição.  
  
## <a name="private-members"></a>Membros particulares  
 Na parte superior da classe **GamePiece**, vários membros particulares são declarados.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privatemembers)]  
  
## <a name="public-properties"></a>Propriedades Públicas  
 Três desses membros particulares são expostos por meio de propriedades públicas. As propriedades **Scale** e **PieceColor** habilitam o aplicativo para especificar a escala e a cor da peça, respectivamente. A propriedade **Bounds** é exposta para permitir que uma peça use os limites de outra para se renderizar, como quando uma peça deve sobrepor outra. O código a seguir mostra a declaração das propriedades públicas.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PublicProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_publicproperties)]  
  
## <a name="class-constructor"></a>Construtor de classe  
 O construtor da classe **GamePiece** aceita os seguintes parâmetros:  
  
-   Um tipo [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx). A referência passada aqui é atribuída ao membro particular `spriteBatch` e é usada para acessar o método [SpriteBatch.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.draw.aspx) quando a peça do jogo se renderiza. Além disso, a propriedade [GraphicsDevice](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.graphicsdevice.aspx) é usada para criar o objeto [Texture](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.texture.aspx) associado à peça do jogo e para obter o tamanho da porta de exibição para detectar quando a peça do jogo encontra um limite de janela para que ela possa pular.  
  
-   Uma cadeia de caracteres que especifica o nome do arquivo da imagem a ser usada para a peça do jogo.  
  
 O construtor também cria um objeto <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> e um objeto <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> e estabelece os manipuladores de eventos para seus eventos.  
  
 O código a seguir mostra o construtor da classe **GamePiece**.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Constructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_constructor)]  
  
## <a name="capturing-mouse-input"></a>Capturando a entrada do mouse  
 O método **UpdateFromMouse** é responsável por detectar quando um botão do mouse é pressionado enquanto o mouse está dentro dos limites da peça do jogo e para detectar quando o botão do mouse foi solto.  
  
 Quando o botão esquerdo do mouse é pressionado (enquanto o mouse está dentro dos limites da peça), este método define um sinalizador para indicar que essa peça do jogo foi capturada pelo mouse e inicia o processamento da manipulação.  
  
 O processamento da manipulação é iniciado com a criação de uma matriz de objetos <xref:System.Windows.Input.Manipulations.Manipulator2D> e com a passagem deles para o objeto <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D>. Isso faz com que o processador de manipulação avalie os manipuladores (nesse caso, um único manipulador) e gere eventos de manipulação.  
  
 Além disso, o ponto no qual a ação de arrastar está ocorrendo é salvo. Isso é usado posteriormente durante o evento <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> para ajustar os valores de translação de delta para que a peça do jogo se desloque na linha atrás do ponto de arrasto.  
  
 Por fim, esse método retorna o estado da captura do mouse. Isso permite que o objeto [GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) gerencie a captura quando há várias peças do jogo.  
  
 O código a seguir mostra o método **UpdateFromMouse**.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_updatefrommouse)]  
  
## <a name="processing-manipulations"></a>Manipulações de processamento  
 Quando a manipulação começa, o evento <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> é gerado. O manipulador para este evento interrompe o processamento de inércia se ele estiver ocorrendo e define o sinalizador *processInertia* como `false`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationStarted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationstarted)]  
  
 Conforme os valores associados à manipulação mudam, o evento <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> é gerado. O manipulador para este evento usa os valores de delta passados nos argumentos de evento para fazer alterações nos valores de rotação e posição da peça do jogo.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationdelta)]  
  
 Quando todos os manipuladores (no caso, um único manipulador) associados a uma manipulação são removidos, o processador de manipulação gera o evento <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed>. O manipulador para este evento inicia o processamento da inércia configurando as velocidades iniciais do processador de inércia para os relatados pelos argumentos de evento e define o sinalizador *processInertia* como `true`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationcompleted)]  
  
## <a name="processing-inertia"></a>Processando a inércia  
 Como o processamento de inércia extrapola novos valores para velocidades lineares e angulares, coordenadas de posição (translação) e rotação, o evento <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> é gerado. O manipulador para este evento usa os valores de delta passados nos argumentos de evento para modificar a posição e a rotação da peça do jogo.  
  
 Se as novas coordenadas resultarem na peça do jogo se movendo além dos limites da porta de exibição, a velocidade do processamento da inércia será revertida. Isso faz com que a peça do jogo pule para fora do limite da porta de exibição que ela encontrou.  
  
 Você não pode alterar as propriedades de um objeto <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> enquanto ele está executando a extrapolação. Portanto, ao reverter a velocidade X ou Y, o manipulador de eventos primeiro para a inércia chamando o método <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Complete%2A>. Ele então atribui os novos valores de velocidade inicial para serem os valores de velocidade atual (ajustados para o comportamento de esponja) e define o sinalizador *processInertia* como `true`.  
  
 O código a seguir mostra o manipulador de eventos para o evento <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta>.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiadelta)]  
  
 Quando o processamento de inércia é concluído, o processador de inércia gera o evento <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Completed>. O manipulador para este evento define o sinalizador *processInertia* como `false`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiacompleted)]  
  
 Nenhuma lógica apresentada até agora, na verdade, faz com que extrapolação de inércia ocorra. Isso é feito no método **ProcessInertia**. Esse método, que é chamado repetidamente do loop de atualização do jogo (o método [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx)) verifica se o sinalizador *processInertia* está definido como `true` e em caso afirmativo, chama o método <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Process%2A>. Chamar esse método causa extrapolação e gera o evento <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta>.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_ProcessInertia](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_processinertia)]  
  
 A peça do jogo não é renderizada realmente até um dos métodos de sobrecarga Draw ser chamado. A primeira sobrecarga desse método é chamada repetidamente do loop de desenho do jogo (o método [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx)). Isso renderiza a peça do jogo com a posição, rotação e fatores de escala atuais.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Draw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_draw)]  
  
## <a name="additional-properties"></a>Propriedades adicionais  
 Três propriedades privadas são usadas pela classe **GamePiece**.  
  
1.  **Timestamp** – obtém um valor de carimbo de data/hora a ser usado pelos processadores de inércia e manipulação.  
  
2.  **X** – obtém ou define a coordenada X da peça do jogo. Ao definir, ajusta os limites usados para teste de clique e a localização dinâmica do processador de manipulação.  
  
3.  **Y** – obtém ou define a coordenada Y da peça do jogo. Ao definir, ajusta os limites usados para teste de clique e a localização dinâmica do processador de manipulação.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privateproperties)]  
  
## <a name="see-also"></a>Consulte também  
 [Manipulações e inércia](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Uso de manipulações e inércia em um aplicativo XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Criação da classe GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Criação da classe Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)
