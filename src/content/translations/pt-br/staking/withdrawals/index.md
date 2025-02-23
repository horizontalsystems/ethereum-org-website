---
title: Saque de staking
description: Página que resume o que são os saques por staking, como eles funcionam e o que os stakers (participantes) precisam fazer para obter suas recompensas
lang: pt-br
template: staking
image: ../../../../../assets/staking/leslie-withdrawal.png
alt: Leslie, o rinoceronte, com suas recompensas de staking
sidebarDepth: 2
summaryPoints:
  - A atualização Shanghai permite os saques de staking no Ethereum
  - Os operadores validadores devem fornecer um endereço de saque para ativá-los
  - As recompensas são distribuídas automaticamente a cada dois ou três dias
  - Validadores que saírem por completo do staking receberão o seu saldo restante
---

<UpgradeStatus dateKey="page-staking-withdrawals-when">
  Os saques de staking serão ativados por meio da atualização Shanghai/Capella. Essa atualização da rede Ethereum deverá ocorrer no primeiro semestre de 2023. <a href="#when" customEventOptions={{ eventCategory: "Anchor link", eventAction: "When's it shipping?", eventName: "click" }}>Mais abaixo</a>
</UpgradeStatus>

A atualização Shanghai/Capella permite **saques de staking** no Ethereum, permitindo que pessoas desbloqueiem recompensas de staking ETH. Os pagamentos de recompensa serão automatica e regularmente enviados para um endereço de saque fornecido e vinculado a cada validador. Os usuários também podem sair totalmente do staking, desbloqueando seu saldo total do validador.

## Recompensas de staking {#staking-rewards}

Os pagamentos de recompensa são processados automaticamente para contas validadoras ativas, com um saldo efetivo máximo de 32 ETH.

Qualquer saldo acima de 32 ETH ganho por meio de recompensas, não contribui realmente para o principal, ou aumenta o peso desse validador na rede e, portanto, é retirado automaticamente como pagamento de recompensa a cada dois ou três dias. Além de fornecer um endereço de saque uma vez, essas recompensas não exigem nenhuma ação do operador validador. Tudo isso é iniciado na camada de consenso, portanto, nenhum gás (taxa de transação) é necessário em nenhuma etapa.

### Como chegamos aqui? {#how-did-we-get-here}

Nos últimos anos, o Ethereum passou por várias atualizações de rede, fazendo a transição para uma rede protegida pelo próprio ETH, em vez da mineração intensiva de energia, como era antes. A participação em consenso no Ethereum agora é conhecida como "staking", pois os participantes têm bloqueado voluntariamente o ETH, colocando-o "em stake" para poder participar da rede. Os usuários que seguem as regras serão recompensados, enquanto as tentativas de trapaça podem ser penalizadas.

Desde o lançamento do contrato de depósito de staking em novembro de 2020, alguns corajosos pioneiros do Ethereum têm bloqueado fundos voluntariamente para ativar os "validadores", as contas que têm o direito de atestar formalmente e propor blocos, seguindo as regras da rede.

Antes da atualização Shanghai, você não podia usar ou acessar seu ETH em stake. Mas agora, você pode optar por receber automaticamente suas recompensas em uma conta fornecida e também pode retirar seu ETH em stake, sempre que você quiser.

### Como me preparo? {#how-do-i-prepare}

<WithdrawalsTabComparison />

### Avisos importantes {#important-notices}

Fornecer um endereço de saque é uma etapa necessária para qualquer conta de validador, antes que ele seja elegível para sacar ETH de seu saldo.

<InfoBanner emoji="⚠️" isWarning>
  <strong>Cada conta de validador só pode ser atribuído a um único endereço de saque, uma vez.</strong> Visto que um endereço é escolhido e enviado para o Beacon Chain, isso não pode ser desfeito ou alterado novamente. Verifique a propriedade e a precisão do endereço fornecido antes de enviar.
</InfoBanner>

Não há <strong>nenhuma ameaça aos seus fundos nesse meio tempo</strong> por não fornecer isso. A falha em adicionar credenciais de saque simplesmente deixará o ETH bloqueado na conta do validador como tem estado até que um endereço de saque seja fornecido.

## Saindo do staking por completo {#exiting-staking-entirely}

Fornecer um endereço de saque é necessário antes que _quaisquer_ fundos possam ser transferidos de um saldo de uma conta do validador.

Os usuários que procuram sair totalmente do staking e sacar seu saldo total de volta, também devem assinar e transmitir uma mensagem de "saída voluntária", com as chaves do validador que iniciarão o processo de saída do staking. Isso é feito com seu cliente validador e enviado ao seu nó beacon, e não requer gás.

O processo de saída de um validador do staking leva uma quantidade variável de tempo, dependendo de quantos outros estão saindo ao mesmo tempo. Uma vez concluída, esta conta não será mais responsável por executar as obrigações de rede do validador, não será mais elegível para recompensas e não terá mais seu ETH "em stake". Nesse momento, a conta será marcada como totalmente "sacável".

Uma vez que uma conta é marcada como "sacável" e as credenciais de saque são fornecidas, não há mais nada que o usuário precise fazer além de esperar. As contas são automática e continuamente varridas por proponentes de bloco para fundos elegíveis de saída, e o saldo da sua conta será transferido integralmente (também conhecido como "saque total") durante a próxima <a href="#validator-sweeping" customEventOptions={{ eventCategory: "Anchor link", eventAction: "Exiting staking entirely (sweep)", eventName: "click" }}>varredura</a>.

## Quando os saques de staking são ativados? {#when}

A funcionalidade de saque será ativada por meio de uma atualização de rede simultânea de duas partes, **Shanghai + Capella**.

<ShanghaiCapella />

## Como funcionam os pagamentos de saque? {#how-do-withdrawals-work}

Se um determinado validador é elegível para um saque ou não é determinado pelo estado da própria conta do validador. Nenhuma entrada de usuário é necessária a um dado momento para determinar se uma conta deveria ter um saque iniciado ou não — todo o processo é realizado automaticamente pela camada de consenso em um loop contínuo.

### Você é o tipo de pessoa que aprende mais com recursos visuais? {#visual-learner}

Confira esta explicação sobre saques de staking do Ethereum pela Finematics:

<YouTube id="RwwU3P9n3uo" />

### Validador de "varredura" {#validator-sweeping}

Quando um validador está agendado para propor o próximo bloco, ele é necessário para construir uma fila de saque de até 16 saques elegíveis. Isso é feito originalmente começando com o validador de índice 0, determinando se há um saque elegível para essa conta, conforme as regras do protocolo, e adicionando-o à fila, se houver. O validador definido para propor o bloco seguinte continuará de onde o último parou, progredindo em ordem indefinidamente.

<InfoBanner emoji="🕛">
Pense em um relógio analógico. O ponteiro do relógio aponta para a hora, avança em uma direção, não pula nenhuma hora e, por fim, volta ao início novamente após o último número ser alcançado.<br/><br/>
Agora, em vez de 1 a 12, imagine que o relógio tenha 0 a N <em>(o número total de contas do validador que já foram registradas na Beacon Chain, mais de 500.000 em janeiro de 2023).</em><br/> <br/>. O ponteiro do relógio aponta para o próximo validador, que precisa ser verificado para saques elegíveis. Começa em 0 e avança ao longo de todo o caminho sem pular nenhuma conta. Quando o último validador é alcançado, o ciclo continua de volta ao início.
</InfoBanner>

#### Verificando os saques de uma conta {#checking-an-account-for-withdrawals}

Enquanto um proponente está verificando os validadores para possíveis saques, cada validador que está sendo verificado é avaliado em relação a uma pequena série de perguntas para determinar se um saque deve ser acionado e, em caso afirmativo, o quanto de ETH deve ser sacado.

1. **Foi fornecido um endereço para saque?** Se nenhum endereço para saque foi fornecido, a conta é ignorada e nenhum saque é iniciado.
2. **O validador saiu e pode ser sacado?** Se o validador saiu completamente, e chegamos à época em que sua conta é considerada "sacável", então um saque total será processado. Isso transferirá todo o saldo restante para o endereço de saque.
3. **O saldo efetivo é maximizado em 32?** Se a conta que tiver credenciais de saque não for completamente encerrada e tiver recompensas acima de 32 em espera, um saque parcial será processado, o qual transfere apenas as recompensas acima de 32 para o endereço de saque do usuário.

Existem apenas duas ações tomadas pelos operadores do validador ao longo do seu ciclo de vida que influenciam diretamente esse fluxo:

- Fornecer credenciais de saque para habilitar qualquer forma de saque
- Sair da rede, o que desencadeará um saque total

### Gás gratuito {#gas-free}

Essa abordagem para saques de staking evita exigir que os stakers (participantes) enviem manualmente uma transação solicitando que uma quantia específica de ETH seja sacada. Isso também significa que **não há gás (taxa de transação) necessário** e os saques também não competem pelo espaço de bloco da camada de execução existente.

### Com que frequência receberei minhas recompensas de staking? {#how-soon}

Um máximo de 16 saques pode ser processado em um único bloco. A esse ritmo, 115.200 saques de validadores podem ser processados por dia (supondo que não haja slots perdidos). Conforme observado acima, os validadores sem saques elegíveis serão ignorados, diminuindo o tempo para concluir a varredura.

Expandindo esse cálculo, podemos estimar o tempo que levará para processar um determinado número de saques:

<TableContainer>

| Número de saques | Tempo de execução |
| :--------------: | :---------------: |
|     400.000      |     3,5 dias      |
|     500.000      |     4,3 dias      |
|     600.000      |     5,2 dias      |
|     700.000      |     6,1 dias      |
|     800.000      |     7,0 dias      |

</TableContainer>

Como você poder ver, isso fica lento à medida que mais validadores estão na rede. Um aumento de blocos perdidos poderia desacelerar isso proporcionalmente, mas isso geralmente representará o lado mais lento dos resultados possíveis.

## Perguntas frequentes {#faq}

<ExpandableCard
title="Após ter fornecido um endereço de saque, posso alterá-lo para um endereço de saque alternativo?"
eventCategory="FAQ"
eventAction="Once I have provided a withdrawal address, can I change it to an alternative withdrawal address?"
eventName="read more">
Não, o processo para fornecer credenciais de saque é um processo único e não pode ser modificado após o envio.
</ExpandableCard>

<ExpandableCard
title="Por que um endereço de saque só pode ser definido uma vez?"
eventCategory="FAQ"
eventAction="Why can a withdrawal address only be set once?"
eventName="read more">
Ao definir um endereço de saque da camada de execução, as credenciais de saque para esse validador foram permanentemente alteradas. Isso significa que as credenciais antigas não funcionarão mais, e as novas credenciais serão direcionadas para uma conta de camada de execução.

Os endereços de saque podem ser ou um contrato inteligente (controlado por seu código), ou uma conta de propriedade externa (EOA, controlada por sua chave privada). Atualmente, essas contas não têm como comunicar uma mensagem de volta para a camada de consenso, que sinalizaria uma mudança nas credenciais do validador, e adicionar essa funcionalidade aumentaria a complexidade do protocolo desnecessariamente.

Uma alternativa para mudar o endereço de saque de um validador específico implicaria os usuários poderem optar por definir um contrato inteligente como seu endereço de saque, o que permitiria lidar com a rotação de chaves, como um cofre. Os usuários que definem seus fundos para seu próprio EOA podem realizar uma saída completa para sacar todos os seus fundos em stake e, em seguida, refazer o stake usando novas credenciais.
</ExpandableCard>

<ExpandableCard
title="E se eu participar de derivativos líquidos de staking ou staking combinado?"
eventCategory="FAQ"
eventAction="What if I participate in liquid staking derivatives or pooled staking"
eventName="read more">

<p>Se você faz parte de um <a href="/staking/pools/">pool de staking</a> ou possui derivativos de staking líquidos, você deve solicitar ao seu provedor mais detalhes sobre como os saques de staking afetarão seu contrato, pois cada serviço opera de forma diferente.</p>
<p>Em geral, os usuários provavelmente não precisam fazer nada, e esses serviços não serão mais limitados pela incapacidade de sacar recompensas ou fundos do validador após essa atualização.</p>
<p>Isso significa que os usuários agora podem decidir resgatar seu ETH subjacente em stake ou alterar o provedor de staking que eles utilizam. Se um pool em particular estiver ficando muito grande, os fundos podem ser sacados, resgatados e recolocados em stake com um <a href="https://pools.invis.cloud">provedor menor</a>. Ou então, se você acumulou ETH suficiente, pode fazer <a href="/staking/solo/">stake em casa</a>.</p>
</ExpandableCard>

<ExpandableCard
title="Os pagamentos de recompensa (saques parciais) acontecem automaticamente?"
eventCategory="FAQ"
eventAction="Do reward payments (partial withdrawals) happen automatically?"
eventName="read more">

<p>Sim, desde que seu validador forneça um endereço de saque. Isso deve ser fornecido uma vez para permitir quaisquer saques, os pagamentos de recompensa serão acionados automaticamente a cada dois ou três dias com cada varredura do validador.</p>
</ExpandableCard>

<ExpandableCard
title="Os saques totais acontecem automaticamente?"
eventCategory="FAQ"
eventAction="Do full withdrawals happen automatically?"
eventName="read more">

<p>Não, se o seu validador ainda estiver ativo na rede, um saque total não acontecerá automaticamente. Isso exige iniciar manualmente uma saída voluntária.</p>
<p>Uma vez que um validador tenha concluído o processo de saída e, supondo que a conta tenha credenciais de saque, o saldo restante será <em>então</em> sacado durante a próxima varredura do validador.</p>
</ExpandableCard>

<ExpandableCard title="Posso sacar uma quantia personalizada?"
eventCategory="FAQ"
eventAction="Can I withdraw a custom amount?"
eventName="read more">

<p>Os saques foram projetados para serem enviados automaticamente, transferindo qualquer ETH que não esteja contribuindo ativamente para o stake. Isso inclui saldos completos para contas. </p>
<p>Não é possível solicitar manualmente o saque de quantidades específicas de ETH.</p>
</ExpandableCard>

<ExpandableCard
title="Eu opero um validador, onde posso encontrar mais informações sobre preparação?"
eventCategory="FAQ"
eventAction="I operate a validator, where can I find more information on preparing?"
eventName="read more">

<p>Operadores de validador são recomendados a visitar a página <a href="https://launchpad.ethereum.org/withdrawals/">Staking Launchpad Withdrawals</a>, onde você encontrará mais detalhes sobre como estar preparado, calendário de eventos e mais detalhes sobre como funcionam os saques.</p>
</ExpandableCard>

<ExpandableCard
title="Posso reativar meu validador depois de sair depositando mais ETH?"
eventCategory="FAQ"
eventAction="Can I re-activate my validator after exiting by depositing more ETH?"
eventName="read more">

<p>Não. Uma vez que um validador tenha saído e seu saldo completo tenha sido sacado, quaisquer fundos adicionais depositados nesse validador serão automaticamente transferidos para o endereço de saque durante a próxima varredura do validador. Para recolocar o ETH em stake, um novo validador deve ser ativado.</p>
</ExpandableCard>

## Leitura adicional {#further-reading}

- [Saques da plataforma de staking](https://launchpad.ethereum.org/withdrawals)
- [EIP-4895: Saques por push da Beacon chain como operações](https://eips.ethereum.org/EIPS/eip-4895)
- [Ethereum Cat Herders - Shanghai](https://www.ethereumcatherders.com/shanghai_upgrade/index.html)
- [PEEPanEIP #94: Saque de ETH em skate (teste) com Potus e Hsiao-Wei Wang](https://www.youtube.com/watch?v=G8UstwmGtyE)
- [PEEPanEIP#68: EIP-4895: Beacon chain envia por push saques como operações com Alex Stokes](https://www.youtube.com/watch?v=CcL9RJBljUs)
- [Entendendo o saldo efetivo do validador](https://www.attestant.io/posts/understanding-validator-effective-balance/)
