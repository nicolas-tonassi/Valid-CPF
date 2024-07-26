# Validacoes de CPF e E-mail
 
## Introdução:
Este projeto foi desenvolvido em sala de aula, com a orientação do professor, como uma forma prática de aplicar os conceitos aprendidos sobre validação de formulários em HTML e JavaScript. O objetivo é garantir que os dados inseridos pelos usuários sejam válidos antes de serem processados.
 
## Validação de CPF:
- Adicionar escutador ao formulário: ✔️
 
   document.getElementById('cpfform').addEventListener('submit', function(event){
       event.preventDefault();
       const cpf = document.getElementById('cpf').value;
       const msg = document.getElementById('message');
       if(validarCPF(cpf)){
           msg.textContent = "O CPF é válido";
msg.style.color = 'green';
       }else{
           msg.textContent = "O CPF é inválido";
msg.style.color = 'red';
       }
   });
 
Descrição: Esta função adiciona um escutador de eventos ao formulário para interceptar a submissão. Quando o formulário é submetido, a função evita a ação padrão (envio do formulário) e executa a função `validarCPF`. Em seguida, exibe uma mensagem indicando se o CPF é válido ou inválido.
 
- Remover caracteres não numéricos: ✔️
 
function validarCPF(cpf){
       cpf = cpf.replace(/[^\d]+/g, ''); //Remove caracteres não numéricos
       // Estrutura de decisão para verificar a quantidade de dígitos e se todos os dígitos são iguais
       if(cpf.length !== 11 || /^(\d)\1{10}$/.test(cpf)){
           return false;
       }
       // Restante do código de validação
   }
 
   Descrição: Dentro da função `validarCPF`, esta linha remove todos os caracteres que não são dígitos do CPF. Isso garante que apenas números sejam considerados na validação.
 
   - Cálculo dos dígitos verificadores:
 
   let soma = 0;
   let resto;
   // validando o primeiro número verificador
   for(let i=1; i <= 9; i++){
       soma += parseInt(cpf.substring(i-1, i)) * (11 - i);
   }
   resto = (soma * 10) % 11;
   if((resto === 10) || (resto === 11)){
       resto = 0;
   }
   if(resto !== parseInt(cpf.substring(9, 10))){
       return false;
   }
   soma = 0;
   // validando o segundo número verificador
   for(let i = 1; i <= 10; i++){
       soma += parseInt(cpf.substring(i-1, i) * (12 - i));
   }
   resto = (soma * 10) % 11;
   if((resto === 10) || (resto === 11)){
       resto = 0;
   }
   if(resto !== parseInt(cpf.substring(10, 11))){
       return false;
   }
   return true;
 
   Descrição: Este trecho calcula os dígitos verificadores do CPF. Primeiro, calcula o primeiro dígito verificador usando os primeiros nove dígitos do CPF. Em seguida, calcula o segundo dígito verificador usando os primeiros dez dígitos. Se qualquer um dos dígitos calculados não coincidir com os dígitos do CPF fornecido, a função retorna `false`.
 
##  Validação de E-mail:
 
- Função de verificação de E-mail:
 
function checarEmail(){
       if(document.forms[0].email.value == "" || document.forms[0].email.value.indexOf('@') == -1 || document.forms[0].email.value.indexOf('.') == -1){
           alert("Por favor, informe um e-mail válido");
           return false;
       }else{
           alert("Email informado");
           document.getElementById('email').innerHTML = document.forms[0].email.value;
       }
   }
 
   Descrição: Esta função verifica se o campo de e-mail está vazio ou se não contém os caracteres '@' ou '.'. Se qualquer uma dessas condições for verdadeira, exibe um alerta pedindo para informar um e-mail válido e retorna `false`.
 
   - Verificar presença de '@' no E-mail:
 
   document.forms[0].email.value.indexOf('@') == -1
 
   Descrição: Esta parte da função `checarEmail` verifica se o e-mail fornecido contém o caractere '@'. Se não contiver, considera o e-mail inválido e exibe uma mensagem de alerta.
 
   - Verificar presença de '.' no E-mail:
 
   document.forms[0].email.value.indexOf('.') == -1
 
   **Descrição**: Similar à verificação de '@', esta linha verifica se o e-mail fornecido contém um ponto ('.'). A ausência deste caractere também resulta em um alerta indicando que o e-mail é inválido.
 
 
 
## Funcionalidades:
 
VALIDAÇÃO DO CPF:
 
- Formulário de entrada: Campo para inserção do CPF.
 
- Verificação de formato: Remoção de caracteres não numéricos.
 
- Cálculo dos dígitos verificadores: Cálculo dos dígitos de verificação para confirmar a validade do CPF.
 
- Mensagens de validação: Exibição de mensagens indicando se o CPF é válido ou inválido.
 
VALIDAÇÃO DE E-MAIL:
 
- Formulário de entrada: Campo para inserção do e-mail.
 
- Verificação de formato: Confirmação da presença de "@" e "." no e-mail.
 
- Mensagens de validação: Alerta ao usuário se o e-mail é válido ou não.
 
## Tecnologias utilizadas:
 
- Visual Studio Code;
- CSS3;
- HTML5;
- JavaScript;
- Git Hub
- Git
 
## Autores:
- [Nicolas Tonassi](https://github.com/nicolas-tonassi)
- [Murilo Tonassi](https://github.com/murilo-tonassi)
- [Pamela Souza](https://github.com/PamelaSouzaSilva)