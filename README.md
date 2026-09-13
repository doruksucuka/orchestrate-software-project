# AI-Managed Software Project Orchestrator

Codex veya Claude Code'un yalnızca kod yazmasını değil; bir yazılım projesini keşif, şartname, planlama, geliştirme, bağımsız QA, kullanıcı kabulü ve production hazırlığı boyunca yönetmesini sağlayan yeniden kullanılabilir Skill.

## Ne sağlar?

- Boş klasör, mevcut repository ve migration projelerini ayrı biçimde ele alır.
- Projeyi riske göre **Light**, **Standard** veya **High Assurance** olarak sınıflandırır.
- Süreç yoğunluğunu ayrıca **Lean**, **Balanced** veya **Maximum** yürütme bütçesiyle ayarlar.
- İş talebini test edilebilir gereksinimlere ve kabul kriterlerine dönüştürür.
- `AGENTS.md`, `CLAUDE.md` ve gerekli proje dokümanlarını AI'ın oluşturup güncel tutmasını sağlar.
- Ürün ve teknik kararlar onaylanmadan geliştirmeye başlamaz.
- Developer ile kaynak kodu değiştiremeyen bağımsız QA oturumunu ayırır.
- Bağımsız QA ile Product Owner kullanıcı kabulünü birbirine karıştırmaz.
- Test kanıtları ve residual riskler olmadan production hazır iddiasında bulunmaz.

Kullanıcı **Product Owner** ve nihai kabul makamıdır. Belgeleri AI hazırlar; kullanıcı yalnızca önemli ürün kararlarını, maddi değişiklikleri ve teslim kararını onaylar.

## İki ayrı ölçek

Güvence profili hangi risklerin kontrol edileceğini belirler. Yürütme bütçesi ise bu kontrolün ne kadar belge, tekrar, oturum ve bağlam maliyetiyle uygulanacağını belirler.

| Yürütme bütçesi | Uygun kullanım |
| --- | --- |
| Lean | Pilotlar, küçük uygulamalar ve token/zaman duyarlı çalışmalar |
| Balanced | Normal müşteri teslimleri ve production hedefli standart projeler |
| Maximum | Yüksek risk, canlı migration ve derin doğrulama gerektiren sistemler |

Örneğin kişisel veri ve yönetici girişi olan küçük bir teklif takip uygulaması **Standard assurance + Lean execution** olarak yürütülebilir. Lean seçim güvenlik veya kabul kriterlerini kaldırmaz; belge tekrarını, gereksiz test çoğaltmayı ve onay turlarını azaltır.

## Çalışma akışı

1. **Discovery & Bootstrap:** İhtiyaçları, varlıkları, güvence profilini ve yürütme bütçesini belirler.
2. **Product Gate:** Davranışları ve ölçülebilir kabul kriterlerini onaylatır.
3. **Technical Gate:** Mimariyi, bağımlılıkları, riskleri ve az sayıdaki dikey artımı onaylatır.
4. **Build:** Onaylı kapsam içinde artımlar arasında yeniden izin istemeden geliştirir.
5. **Independent QA:** Sabit revision'ı ayrı ve salt-okunur bağlamda inceler.
6. **Triage & Targeted Retest:** Gerçek bulguları ayıklar; dar düzeltmeden sonra yalnız ilgili riski yeniden doğrular.
7. **User Acceptance & Release:** Kullanıcının ürünü görmesini sağlar; yerel kabul ile production yetkisini ayrı tutar.

## Kurulum

Repository özel olduğu için GitHub hesabınızın terminalde yetkilendirilmiş olması gerekir.

### Codex ve Claude Code'a tek komutla kurulum

[`skills`](https://skills.sh) CLI, Skill'i global olarak kurar ve iki aracın doğru dizinlerini otomatik yönetir:

```bash
npx skills add https://github.com/doruksucuka/orchestrate-software-project \
  --skill orchestrate-software-project \
  --global \
  --agent codex \
  --agent claude-code \
  --yes
```

### Yalnızca Codex

```bash
npx skills add https://github.com/doruksucuka/orchestrate-software-project \
  --skill orchestrate-software-project --global --agent codex --yes
```

### Yalnızca Claude Code

```bash
npx skills add https://github.com/doruksucuka/orchestrate-software-project \
  --skill orchestrate-software-project --global --agent claude-code --yes
```

Kurulumu doğrulamak için:

```bash
npx skills list --global
```

## Kullanım

Codex:

```text
$orchestrate-software-project
```

Claude Code:

```text
/orchestrate-software-project
```

Örnek başlangıç talebi:

```text
Yeni bir projeye başlıyoruz. Bu boş klasörde süreci uçtan uca yönet.
Uygun güvence profilini ve yürütme bütçesini öner.
Ürün ve teknik kararlar onaylanmadan uygulama kodu yazma.
```

Belirli bir bütçe doğrudan da istenebilir:

```text
Bu küçük projeyi Standard assurance + Lean execution ile yönet.
Gerekli güvenlik ve QA kontrollerini koru; belgeleri, onay turlarını,
handoff'ları ve durum yanıtlarını mümkün olduğunca kısa tut.
```

Skill, kapsamlı proje başlatma ve yönetme taleplerinde otomatik olarak da seçilebilir. Tek dosyalık düzenlemeler veya dar kapsamlı hata düzeltmeleri için tasarlanmamıştır.

## Güncelleme

```bash
npx skills update orchestrate-software-project --global --yes
```

## Repository yapısı

```text
orchestrate-software-project/
├── README.md
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── delivery-lifecycle.md
    ├── execution-budgets.md
    ├── executor-adapters.md
    └── risk-profiles.md
```

## Önemli sınır

Bu Skill; hukuk, mevzuat, sızma testi, güvenlik uzmanlığı veya alan uzmanlığı gerektiren profesyonel kontrollerin yerine geçmez. Yüksek riskli projelerde gerekli insan uzman incelemelerini sürece dahil eder.
