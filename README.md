/**
 * @nome PerfilProfissional
 * @autor EhsanDavari
 * @autorId 553139953597677568
 * @versão 1.0.3
 * @description com este plugin: Você pode copiar o banner do usuário (cor do banner e foto do banner) Você pode copiar a foto do perfil do usuário Você pode copiar Sobre mim para o usuário Você também pode copiar a biografia do usuário
 * @convidar xfvHwqXXKs
 * @site https://www.beheshtmarket.com
 * @fonte https://github.com/iamehsandvr/ProProfile
 * @updateUrl https://raw.githubusercontent.com/iamehsandvr/ProBanner/main/ProProfile.plugin.js
 */

const solicitação = require("solicitação");
const fs = requer("fs");
const caminho = require("caminho");

const configuração = {
  informação: {
    nome: "ProProfile",
    autores: [
      {
        nome: "EhsanDavari",
      },
    ],
    versão: "1.0.3",
    descrição:
      "com este plugin: Você pode copiar o banner do usuário (cor do banner e foto do banner) Você pode copiar a foto do perfil do usuário Você pode copiar Sobre mim para o usuário Você também pode copiar a biografia do usuário",
    registro de alterações: [
      {
        título: "Atualização legal",
        tipo: "melhorado",
        Unid: [
          "Clique duas vezes para copiar o perfil do servidor",
          "Clique duas vezes para copiar o banner do servidor",
          "Ø¨Ø±Ø§ÛŒ Ú©Ù¾ÛŒ Ú©Ø±Ø¯Ù† Ù¾Ø±ÙˆÙ Ø§ÛŒÙ„ Ø³Ø±ÙˆØ± Ø¯ÙˆØ¨Ø§Ø± Ú©Ù„ÛŒÚ© Ú©Ù†ÛŒØ¯",
          "Ø¨Ø±Ø§ÛŒ Ú©Ù¾ÛŒ Ú©Ø±Ø¯Ù† Ø¨Ù†Ø± Ø³Ø±ÙˆØ± Ø¯ÙˆØ¨Ø§Ø± Ú©Ù„ÛŒÚ© Ú©Ù†ÛŒØ¯" ,
        ],
      },
    ],
  },
};

módulo.exportações = !global.ZeresPluginLibrary
  ? aula {
      construtor() {
        this._config = configuração;
      }

      carregar() {
        BdApi.showConfirmationModal(
          "É necessário um plugin de biblioteca",
          `O plugin de biblioteca necessário para o PluginBuilder do AQWERT está faltando. Clique em Baixar agora para instalá-lo.`,
          {
            confirmText: "Baixar",
            cancelText: "Cancelar",
            emConfirmar: () => {
              solicitação.obter(
                "https://rauenzi.github.io/BDPluginLibrary/release/0PluginLibrary.plugin.js",
                (erro, resposta, corpo) => {
                  se (erro)
                    retornar electron.shell.openExternal(
                      "https://betterdiscord.net/ghdl?url=https://raw.githubusercontent.com/rauenzi/BDPluginLibrary/master/release/0PluginLibrary.plugin.js"
                    );

                  fs.writeFileSync(
                    caminho.join(BdApi.Plugins.pasta, "0PluginLibrary.plugin.js"),
                    corpo
                  );
                }
              );
            },
          }
        );
      }

      começar() {}

      parar() {}
    }
  : (([Plugin, Biblioteca]) => {
      constante {
        Módulos Discord,
        Módulos Webpack,
        Remendador,
        Utilitários de plugin,
        Brindes,
      } = Biblioteca;
      const { Módulo Eletrônico, React } = Módulos Discord;
      classe plugin estende Plugin {
        construtor() {
          super();
        }
        onStart() {
          este.ProProfile();
        }

        onParar() {
          Patcher.unpatchAll();
        }
        ProProfile() {
          const NomeTag = WebpackModules.find(
            (m) => m?.default?.displayName === "Etiqueta de Nome"
          );
          const UserBio = WebpackModules.find(
            (m) => m?.default?.displayName === "Biografia do Usuário"
          );
          const UserBanner = WebpackModules.find(
            (m) => m?.default?.displayName === "Banner do Usuário"
          );
          const CustomStatus = WebpackModules.find(
            (m) => m?.default?.displayName === "Status personalizado"
          );
          document.addEventListener("dblclick", ({ alvo }) => {
            se (novo RegExp(/guild*/).test(target.dataset.listItemId)) {
              global.ZLibrary.DiscordModules.ElectronModule.copy(
                alvo.crianças[0].currentSrc.replace(/([0-9]+)$/, "4096")
              );
              return BdApi.showToast(`Link do ícone do servidor copiado com sucesso`, {
                tipo: "sucesso",
              });
            } senão se (
              novo RegExp(/animatedBannerHoverLayer*/).test(target.className)
            ) {
              global.ZLibrary.DiscordModules.ElectronModule.copy(
                `https://cdn.discordapp.com/banners/${target.__reactFiber$.return.memoizedProps.guild.id}/${target.__reactFiber$.return.memoizedProps.guildBanner}.gif?size=4096`
              );
              retornar BdApi.showToast(`Link do banner do servidor copiado com sucesso`, {
                tipo: "sucesso",
              });
            } senão se (novo RegExp(/height:*/).test(target.style.cssText)) {
              var strGuildBanner = document.getElementsByClassName(
                "animadoContainer-2laTjx"
              );
              global.ZLibrary.DiscordModules.ElectronModule.copy(
                strGuildBanner[0].crianças[0].crianças[0].currentSrc.replace(
                  /([0-9]+)$/,
                  "4096"
                )
              );
              return BdApi.showToast(`Link do ícone do servidor copiado com sucesso`, {
                tipo: "sucesso",
              });
            }
          });
          document.addEventListener("clique", ({ alvo }) => {
            se (
              alvo.ariaLabel &&
              target.style.cssTexto &&
              novo RegExp(/avatar\-3QF_VA/).teste(alvo.nomedaclasse)
            ) {
              deixe MemberProfileUrl =
                alvo.__reactProps$.crianças.props.crianças[0].props
                  .crianças[0].props.crianças.props.src;
              MemberProfileUrl = novo RegExp(/ativos/).teste(MemberProfileUrl)
                ? `https://discord.com${MemberProfileUrl}`
                : MemberProfileUrl.replace(/([0-9]+)$/, "4096");
              global.ZLibrary.DiscordModules.ElectronModule.copy(
                URL do perfil do membro
              );
              retornar BdApi.showToast(`Link da imagem do perfil do usuário criado com sucesso`, {
                tipo: "sucesso",
              });
            }
          });
          Patcher.after(NameTag, "padrão", (_, [props], ret) => {
            ret.props.estilo = {
              cursor: "ponteiro",
            };
            ret.props.onClick = (_) => {
              ElectronModule.copy(`${props.name}#${props.discriminator}`);
              Brindes.sucesso(
                `Nome de usuário copiado com sucesso para <strong>${props.name}</strong>!`
              );
            };
          });
          Patcher.after(UserBanner, "padrão", (_, [props], ret) => {
            ret.props.onClick = (_) => {
              //deixe ClassBanner = BdApi.findModuleByProps("banner", "bannerOverlay")
              se (
                _.target.classList.contains("banner-1YaD3N") &&
                _.target.style.imagem de fundo
              ) {
                deixe BannerUrl = _.target.style.backgroundImage;
                BannerUrl = BannerUrl.substring(
                  4,
                  BannerUrl.comprimento - 1
                ).substituir(/["']/g, "");
                BannerUrl = BannerUrl.substituir(
                  /(?:\?tamanho=\d{3,4})?$/,
                  "?tamanho=4096"
                );
                Módulo Eletrônico.copy(BannerUrl);
                return Toasts.success("O link do banner foi copiado com sucesso");
              } senão se (_.target.style.backgroundColor) {
                const ColorCode = _.target.style.backgroundColor;
                var RGBColorCode = ColorCode.replaceAll(
                  /[az() ]+/gi,
                  ""
                ).dividir(",");
                const RGB2HEX = {
                  r: Número(RGBColorCode[0]).toString(16),
                  g: Número(RGBColorCode[1]).toString(16),
                  b: Número(RGBColorCode[2]).toString(16),
                };
                const CódigoCorHexadecimal =
                  "#" +
                  (RGB2HEX.r.comprimento == 1 ? 0 + RGB2HEX.r : RGB2HEX.r) +
                  (RGB2HEX.g.comprimento == 1 ? 0 + RGB2HEX.g : RGB2HEX.g) +
                  (RGB2HEX.b.comprimento == 1 ? 0 + RGB2HEX.b : RGB2HEX.b);
                ElectronModule.copy(CódigoHexadecimalCor);
                retornar Toasts.success(
                  `Código de cor hexadecimal: ${ColorHexCode} foi copiado com sucesso`
                );
              }
            };
            document.addEventListener("clique", (alvo) => {
              se (target.ariaLabel && target.style.cssText) {
                deixe MemberProfileUrl =
                  alvo.__reactProps$.crianças.props.crianças[0].props.crianças
                    .props.src;
                MemberProfileUrl = novo RegExp(/ativos/).teste(MemberProfileUrl)
                  ? `https://discord.com${MemberProfileUrl}`
                  : MemberProfileUrl.replace(/([0-9]+)$/, "4096");
                global.ZLibrary.DiscordModules.ElectronModule.copy(
                  URL do perfil do membro
                );
                retornar BdApi.showToast(`Link da imagem do perfil do usuário criado com sucesso`, {
                  tipo: "sucesso",
                });
              }
            });
          });
          Patcher.after(UserBio, "padrão", (_, [props], ret) => {
            ret.props.estilo = {
              cursor: "ponteiro",
            };
            ret.props.onClick = (_) => {
              Módulo Eletrônico.copy(props.userBio);
              Toasts.success(`<strong>Biografia do usuário</strong> copiada com sucesso! `);
            };
          });
          Patcher.after(CustomStatus, "padrão", (_, [props], ret) => {
            ret.props.estilo = {
              cursor: "ponteiro",
            };
            ret.props.onClick = (_) => {
              "estado" em props.activity && !("emoji" em props.activity)
                ? Módulo Eletrônico.copy(`${props.activity.state}`)
                : "emoji" em props.activity && "estado" em props.activity
                ? Módulo Eletrônico.copy(
                    `${props.activity.emoji.name} ${props.activity.state}`
                  )
                : Módulo Eletrônico.copy(`${props.activity.emoji.name}`);
              Brindes.sucesso(
                `<strong>Status do usuário</strong> copiado com sucesso!`
              );
            };
          });
        }
      }

      retornar plugin;
    })(global.ZeresPluginLibrary.buildPlugin(config));
