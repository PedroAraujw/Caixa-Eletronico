# DOCUMENTO DE REQUISITOS
Um banco local pretende instalar um novo caixa eletrônico (automated teller machine - ATM) para permitir que os usuários realizem transações financeiras básicas. Cada usuário pode ter somente uma conta no banco. Os usuários do ATM devem ser capazes de vizualizar seus saldos bancários, sacar dinheiro (isto é, retirar dinheiro de uma conta) e depositar fundos (isto é, colocar dinheiro em uma conta).
    A interface com o usuário do caixa eletrônico contém os seguintes componentes de hardware:
    - uma tela que exibe uma mensagem de boas-vindas;
    - um teclado que recebe a entrada numérica dó usuário;
    - um dispensador de cédulas que disponibiliza dinheiro para os usuários;
    - uma abertura para depósito que recebe os envelopes com depósito do usuário. 
O dispensador de cédulas é carregado diariamente com $500 em notas de $20 [Nota: Devido ao escopo limitado desse estudo de caso, certos elementos do ATM descritos aqui não simulam exatamente aqueles de um ATM real. Por exemplo, um ATM real em geral contém um dispositivo que lê o número da conta de um usuário a partir de um cartão ATM, enquanto esse ATM solicita que o usuário digite o número de uma conta no teclado. Normalmente, um ATM real também imprime um recibo no fim de uma sessão, mas toda a saída desse ATM aparece na tela.]
O banco quer que você desenvolva um software para realizar as transações financeiras iniciadas pelos clientes do banco por meio do ATM. O banco integrará o software com o hardware do ATM em um momento posterior. O software deve encapsular a funcionalidade dos dispositivos de hardware (por exemplo, o dispensador de cédulas, a abertura para depósito) dentro dos componentes de sofware, mas ele próprio não precisa se preocupar com a maneira como esses dispositivos realizam suas tarefas. O hardware do ATM ainda não foi desenvolvido; assim, em vez de escrever seu fotware para ser exectado no ATM, você deve desenvolver uma primeira versão do software para executar em um computador pessoal. Essa versão deve utilizar o monitor do computador para simular a tela do ATM  e o teclado do computador para simular o teclado do ATM. 
Uma sessão do ATM consiste na autenticação de um usuário (isto é, provar a identidade do usuário) com base em um número de conta e número pessoal de identificação (personal identification number – PIN) para então criar e executar as transações financeiras. Para autenticar um usuário e realizar transações, o ATM deve interagir com o banco de dados de informações de conta do banco. Para cada conta bancária, o banco de dados armazena um número de conta, um PIN e um saldo que indica a quantia de dinheiro na conta. [Nota: Por simplicidade, supomos que o
banco planeja construir somente um ATM, portanto não precisamos nos preocupar com múltiplos ATMs acessando esse banco de dados ao mesmo tempo. Além disso, supomos que o banco não faz nenhuma alteração nas informações no banco de dados enquanto um usuário está acessando o ATM. Além disso, fazemos a suposição simplificadora de que o banco confia no ATM para acesso e manipulação das informações no banco de dados sem medidas de segurança significativas.]
Ao acessar inicialmente o ATM, o usuário deve experimentar a seguinte seqüência de eventos:
    1. A tela exibe uma mensagem de boas-vindas e solicita que o usuário insira o número da conta.
    2. O usuário insere um número de conta de cinco dígitos utilizando o teclado numérico.
    3. A tela solicita que o usuário insira o PIN associado com o número da conta especificada.
    4. O usuário insere um PIN de cinco dígitos utilizando o teclado numérico.
    5. Se o usuário inserir um número de conta válida e o PIN correto para essa conta, a tela exibe o menu principal. Se o usuário inserir um número inválido de conta ou um PIN incorreto, a tela exibe uma mensagem apropriada e então o ATM retorna ao Passo 1 para reiniciar o processo de autenticação. Depois que o ATM autentica o usuário, o menu principal exibe uma opção numerada para cada um dos três tipos de transações: consulta de saldos (opção 1), retirada (opção 2) e depósito (opção 3). O menu principal também exibe uma opção que permite ao usuário sair do sistema (opção 4). O usuário então opta por realizar uma transação (inserindo 1, 2 ou 3) ou sair do sistema (inserindo 4). Se o usuário inserir uma opção inválida, a tela exibe uma mensagem de erro e, então, reexibe o menu principal. Se o usuário inserir 1 para fazer uma consulta de saldos, a tela exibe o saldo da conta do usuário. Para fazer isso, o ATM deve recuperar o saldo a partir do banco de dados do banco.

--- 
  Main menu:
        1 - View my balance
        2 - Withdraw cash
        3 - Deposit funds
        4 - Exit
    Enter a choice:
        Take cash here
        Insert deposit envelope here
 *Menu principal do ATM.*
---

**As seguintes ações ocorrem quando o usuário insere 2 para fazer uma retirada:**
    6. A tela exibe um menu que contém quantias-padrão de saque: $ 20 (opção 1), $ 40 (opção 2), $ 60 (opção 3), $ 100 (opção 4) e $ 200 (opção 5). O menu também contém uma opção para permitir que o usuário cancele a transação (opção 6).
    7. O usuário insere uma seleção de menu (1–6) utilizando o teclado.
    8.Se a quantia de saque escolhida for maior que o saldo da conta do usuário, a tela exibe uma mensagem declarando isso e solicitando que o usuário escolha uma quantia menor. O ATM então retorna ao Passo 1. Se a quantia de saque escolhida for menor ou igual ao saldo da conta do usuário (isto é, uma quantia de retirada aceitável), o ATM prossegue para o Passo 4. Se o usuário optar por cancelar a transação (opção 6), o ATM exibe o menu principal (Figura 2.16) e espera pela entrada do usuário.
    9.Se o dispensador de cédulas contiver dinheiro suficiente para atender à solicitação, o ATM prossegue para o Passo 5. Do con-
trário, a tela exibe uma mensagem indicando o problema e solicitando que o usuário escolha uma quantia de saque menor. O ATM retorna então ao Passo 1.

---
Withdrawal options:
 1 - $20 4 - $100
 2 - $40 5 - $200
 3 - $60 6 - Cancel transaction
Choose a withdrawal option (1-6):
    Take cash here
    Insert deposit envelope here
 *Menu de saque do ATM.*
---

    10. O ATM debita (isto é, subtrai) a quantia de saque do saldo da conta do usuário no banco de dados do banco.
    11. O dispensador de cédulas entrega a quantia de dinheiro desejada para o usuário.
    12. A tela exibe uma mensagem lembrando o usuário de pegar o dinheiro.

**As seguintes ações ocorrem quando o usuário insere 3 (enquanto o menu principal é exibido) para efetuar um depósito:**
    13. A tela solicita que o usuário insira uma quantia de depósito ou que digite 0 (zero) para cancelar a transação.
    14. O usuário insere uma quantia de depósito ou 0 utilizando o teclado numérico. [Nota: O teclado não contém um ponto de fração decimal nem um sinal de cifrão, portanto o usuário não pode digitar uma quantia monetária real (por exemplo, $ 1,25). Em vez disso, o usuário deve inserir uma quantia de depósito como um número de centavos (por exemplo, 125). O ATM divideentão esse número por 100 para obter um número que represente uma quantia monetária (por exemplo, 125 ÷ 100 = 1,25).]
    15. Se o usuário especificar uma quantia de depósito, o ATM prossegue para o Passo 4. Se o usuário optar por cancelar a transação (inserindo 0), o ATM exibe o menu principal e espera pela entrada do usuário.
    16. A tela exibe uma mensagem solicitando que o usuário insira um envelope de depósito na abertura de depósito.
    17. Se a abertura de depósito receber um envelope de depósito dentro de dois minutos, o ATM credita (isto é, adiciona) a quantia de depósito ao saldo de conta de usuário no banco de dados do banco. [Nota: Essa quantia não permanece imediatamente disponível para saque. Primeiro o banco deve verificar fisicamente a quantia de dinheiro no envelope de depósito e quaisquer cheques no envelope devem ser transferidos do emissor do cheque para a conta do depositário. Quando qualquer um desses eventos ocorrer, o banco atualiza apropriadamente o saldo do usuário armazenado no seu banco de dados. Isso ocorre independentemente do sistema ATM.] Se a abertura para depósito não receber o envelope de um depósito dentro desse período, a tela exibe uma mensagem informando que o sistema cancelou a transação devido à inatividade. O ATM exibe então o menu principal e espera a entrada do usuário.
Depois que o sistema realiza com sucesso uma transação, ele deve reexibir o menu principal para que o usuário possa realizar outras transações. Se o usuário escolher sair do sistema (opção 4), a tela exibe uma mensagem de agradecimento e então exibe a mensagem de boas-vindas para o próximo usuário.
