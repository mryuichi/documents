This text will be intended to insert the ITU-T summery document that are under discussion of the PR in TF-UC after approved.

* [ITU-T Y.4409/Y.2070 (01/2015) - Requirements and architecture of the home energy management system and home network services](https://www.itu.int/ITU-T/recommendations/rec.aspx?id=12420&lang=en)


## Y.4409/Y.2070 - Requirements and architecture of the home energy management system and home network services
**Key points in abstract:**


A key concept
多様なデバイスをWebインタフェースにすること。アプリケーションはWebアプリケーションで実行できるように、クラウドもしくはホーム内で変換する。
ホームネットワークをスコープにしているが、ホームに関わるプロトコルを対処にしただけで、他の領域でもあまり遜色は内。検討すべきプロトコル数が増えるため、押さえられている。SUｐ57には記載s例照る。
これは、Y.sup57に調査されたBARNETのようなプロトコルでも対応可能であるとすることから、示される

この勧告では、W3C WoTと同様に印フォーメーショモデルが導入されて、それに対する操作がWebインタフェースの基本となっている。そのため、その
インタフェースに合うようにゲートウェイでは変換を行う。特に、建物内のネットワークは、無線やRS485のようなLayer2のインタフェースが使われることもあり、
こうした装置をLayer 7のWebインタフェースに合わせることが必要である。

The other key differences between this recommendation and W3C WoT architectures:

* intermediaryを含むアーキテクチャが前提になっている
* 装置のインタフェースについて詳細が記載されている。ここからインタラクションあふぉーだんすとして、PROPERTYとEVENTが必要と記載されている。
* Information modelの操作としてACTIONがない。これは、装置に使われているインタフェースからきたもの。当時の実証実験でもACTIONに対応するモノがなかった。
* Management
* Security抽象レベルで記載

** User cases:**
本文中とAppendix

Additional refereneces:
* [ITU-T Y.Suppl.57 (12/2019) - Implementation guidelines to Recommendation ITU-T Y.4409/Y.2070](https://www.itu.int/ITU-T/recommendations/rec.aspx?id=14175&lang=en)
