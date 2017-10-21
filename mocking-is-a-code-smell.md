翻訳: <https://medium.com/javascript-scene/mocking-is-a-code-smell-944a70c90a6a>.

# モッキングはコードの臭い (Mocking is a Code Smell)

> One of the biggest complaints I hear about TDD and unit tests is that people struggle with all of the mocking required to isolate units. Some people struggle to understand how their unit tests are even meaningful. In fact, I’ve seen developers get so lost in mocks, fakes, and stubs that they wrote entire files of unit tests where no actual implementation code was exercised at all. Oops.

私がTDDとユニットテストに関して耳にするもっとも大きな不平のひとつは、人々がユニットを分離するために必要とされるすべてのモッキングと悪戦苦闘していることです。ある人々は彼らのユニットテストがどうしたらなおも意味のあるものとなるのかを理解するに苦労しています。事実、私は開発者たちがユニットテストのファイル全体で書いたモック、フェイク、スタブで途方にくれるのを見てきました。そこでは、*実際の実装コードはまったく鍛えられない*、というのに。やれやれ。

> On the other end of the spectrum, it’s common to see developers get so sucked into the dogma of TDD that they think they absolutely must achieve 100% code coverage, by any means necessary, even if that means they have to make their codebase more complex to pull it off.

スペクトルの反対側では、彼らが絶対に、*なんとしてでも*、コードカバレッジ100%を達成しなければならないと考えている、TDDの教義に吸い込まれていく開発者を見るのがふつうです。たとえそのことが、うまくやるためには彼らのコードベースをより複雑にしなければならないことを意味するのだとしてもです。

> I frequently tell people that mocking is a code smell, but most developers pass through a stage in their TDD skills where they want to achieve 100% unit test coverage, and can’t imagine a world in which they do not use mocks extensively. In order to squeeze mocks into their application, they tend to wrap dependency injection functions around their units or (worse), pack services into dependency injection containers.

私はよく人々にモッキングはコードの臭いだと伝えますが、ほとんどの開発者はユニットテストカバレッジ100%を達成したいというTDDスキルのステージを通過し、モックを広範囲に使わないという世界を想像することができません。モックを彼らのアプリケーションに詰め込むために、彼らのユニットの周りを依存性注入関数でラップするか、または（さらに悪いことに）、サービスを依存性注入コンテナにパックしがちです。

> Angular takes this to an extreme by baking dependency injection right into all Angular component classes, tempting users to view dependency injection as the primary means of decoupling. But dependency injection is not the best way to accomplish decoupling.

Angular は、すべての Angular コンポーネントクラスの中に依存性注入を膨らませ、ユーザーが依存性注入を疎結合の主な手段とみなすように仕向けることによって、これを極端に推し進めます。しかし、依存性注入は疎結合を達成する最善の方法ではありません。

## TDDはより良い設計につながるべき (TDD should lead to better design)

>> The process of learning effective TDD is the process of learning how to build more modular applications.

> 効果的なTDDを学ぶというプロセスは、よりモジュール化されたアプリケーションをどうやって構築するかを学ぶプロセスである。

> TDD tends to have a simplifying effect on code, not a complicating effect. If you find that your code gets harder to read or maintain when you make it more testable, or you have to bloat your code with dependency injection boilerplate, you’re doing TDD wrong.

TDDはコードにおいて単純化する効果をもつ傾向にあります、複雑化する効果ではなく。もしあなたが、自分のコードをテストしやすくするときにコードが読むのも保守するのも難しくなっていることを見つけるのであれば、または依存性注入の定型コードであなたのコードを膨らませなければならないのであれば、あなたはTDDを間違ったやり方でおこなっています。

> Don’t waste your time wedging dependency injection into your app so you can mock the whole world. Chances are very good that it’s hurting you more than it’s helping. Writing more testable code should simplify your code. It should require fewer lines of code and more readable, flexible, maintainable constructions. Dependency injection has the opposite effect.

あなたが全世界をモックすることができるからといって、依存性注入をあなたのアプリに打ち込むことに時間を浪費してはいけません。あなたを助ける以上に傷つける可能性が高いです。よりテストしやすいコードを書くことは、コードを単純化するはずです。それは、より少ない行のコードと、より読みやすく、柔軟で、保守しやすい構造を要求するはずです。依存性注入には反対の効果があります。

> This text exists to teach you two things:
>
> 1. You can write decoupled code without dependency injection, and
> 2. Maximizing code coverage brings diminishing returns — the closer you get to 100% coverage, the more you have to complicate your application code to get even closer, which can subvert the important goal of reducing bugs in your application.

この文章はあなたに2つのことを教えるためにあります：

1. あなたは依存性注入なしで疎結合なコードを書くことができます。そして、
2. コードカバレッジの最大化は利益減少をもたらします。つまり、カバレッジ100%に近づけば近づくほど、ますますあなたのアプリケーションコードを複雑にしなければならなくなります。それはあなたのアプリケーションのバグを減らすという重要な目標を覆す可能性があるのです。

> More complex code is often accompanied by more cluttered code. You want to produce uncluttered code for the same reasons you want to keep your house tidy:
>
> - More clutter leads to more convenient places for bugs to hide, which leads to more bugs, and
> - It’s easier to find what you’re looking for when there’s less clutter to get lost in.

より複雑なコードは、しばしばより乱雑なコードを伴います。あなたは、自分の家をきれいにしたいのと同じ理由で、整然としたコードを生み出したいと考えます：

1. より乱雑なコードは、バグが隠れるためのより便利な場所につながり、それはより多くのバグにつながります。そして、
2. 迷子になるような乱雑さが少ないときには、探しているものを見つけるのはより簡単です。

## コードの臭いとは？ (What is a code smell?)

>> “A code smell is a surface indication that usually corresponds to a deeper problem in the system.” ~ Martin Fowler

> 「コードの臭いは、通常システムのより深い問題に対応する、表面的な兆候です。」- マーチン・ファウラー

> A code smell does not mean that something is definitely wrong, or that something must be fixed right away. It is a rule of thumb that should alert you to a possible opportunity to improve something.

コードの臭いは、何かがはっきりと悪い、もしくは何かがすぐに修正されなければならない、ということを意味しません。それは、何かを改善するための可能な機会に対してあなたに警告するはずの、おおざっぱなルールなのです。

> This text and its title in no way imply that all mocking is bad, or that you should never mock anything.

この文章とタイトルは、すべてのモッキングが悪い、もしくは何もモックしてはならない、ということを示唆するものでは決してありません。

> Additionally, different types of code need different levels (and different kinds) of mocks. Some code exists primarily to facilitate I/O, in which case, there is little to do other than test I/O, and reducing mocks might mean your unit test coverage would be close to 0.

加えて、異なるコードのタイプは、モックの異なるレベル（と異なる種類）を必要とします。あるコードは主にI/Oを容易にするために存在し、その場合、I/Oをテストするより他にすることはほとんどありません。そして、モックを減らすことは、あなたのテストカバレッジがゼロに近づくことを意味するかもしれません。

> If there is no logic in your code (just pipes and pure compositions), 0% unit test coverage might be acceptable, assuming your integration or functional test coverage is close to 100%. However, if there is logic (conditional expressions, assignments to variables, explicit function calls to units, etc…), you probably do need unit test coverage, and there may be opportunities to simplify your code and reduce mocking requirements.

もしあなたのコードにロジックがなければ（単なるパイプと純粋なコンポジション）、ユニットテストカバレッジ0%は受け入れられるでしょう、仮にあなたの結合テストまたは機能テストカバレッジが100%に近いとするならば。しかし、もしロジック（条件分岐、変数への代入、ユニットへの明示的な関数呼び出し、など）があれば、あなたはおそらくテストカバレッジを本当に必要とするし、コードを単純化してモックの必要性を減らす機会があるかもしれません。

## モックとは？ (What is a mock?)

> A mock is a test double that stands in for real implementation code during the unit testing process. A mock is capable of producing assertions about how it was manipulated by the test subject during the test run. If your test double produces assertions, it’s a mock in the specific sense of the word.

モックとは、ユニットテスト処理中に実際の実装コードの代わりをする、テストダブルのことです。モックは、テスト実行中にテスト対象によってどのように操作されたかについてのアサーションを、生成することができます。もしあなたのテストダブルがアサーションを生成するならば、それは言葉の特定の意味でのモックのことです。

> The term “mock” is also used more generally to refer to the use of any kind of test double. For the purpose of this text, we’ll use the words “mock” and “test double” interchangeably to match popular usage. All test doubles (dummies, spies, fakes, etc…) stand in for real code that the test subject is tightly coupled to, therefore, all test doubles are an indication of coupling, and there may be an opportunity to simplify the implementation and improve the quality of the code under test. At the same time, eliminating the need for mocking can radically simplify the tests themselves, because you won’t have to construct the mocks.

「モック」という用語はまた、より一般的には、あらゆる種類のテストダブルの使用を指すために使われます。この文章の目的のため、私たちは「モック」と「テストダブル」という言葉を一般的な用法に合わせるために交換可能なものとして使います。すべてのテストダブル（ダミー、スパイ、フェイク、など）は、テスト対象が密結合となっている実際のコードの代わりをします。それゆえ、すべてのテストダブルは結合のしるしであり、実装を単純化しテスト対象のコードの質を改善する機会かもしれません。同時に、モッキングの必要性を除去することはテストそれ自体を根本的に単純化することができます、なぜならあなたはモックを構築する必要がないからです。

## ユニットテストとは？ (What is a unit test?)

> Unit tests test individual units (modules, functions, classes) in isolation from the rest of the program.

ユニットテストは、個々のユニット（モジュール、関数、クラス）をプログラムの残りの部分から隔離された状態でテストします。

> Contrast unit tests with integration tests, which test integrations between two or more units, and functional tests, which test the application from the point of view of the user, including complete user interaction workflows from simulated UI manipulation, to data layer updates, and back to the user output (e.g., the on-screen representation of the app). Functional tests are a subset of integration tests, because they test all of the units of an application, integrated in the context of the running application.

ユニットテスト、2つ以上のユニット間の連携をテストする結合テスト、そして、ユーザー視点からアプリケーションをテストする機能テストを、対比してください。機能テストは、シミュレートされたUI操作から、データレイヤーの更新、さらにユーザーへの結果表示（例えば、アプリのオンスクリーン表示）という完全なユーザーインタラクションワークフローを含みます。機能テストは結合テストのサブセットです、なぜなら、実行中のアプリケーションコンテキストに統合された、アプリケーションの全ユニットをテストするからです。

> In general, units are tested using only the public interface of the unit (aka “public API” or “surface area”). This is referred to as black box testing. Black box testing leads to less brittle tests, because the implementation details of a unit tend to change more over time than the public API of the unit. If you use white box testing, where tests are aware of implementation details, any change to the implementation details could break the test, even if the public API continues to function as expected. In other words, white-box testing leads to wasted rework.

一般的に、ユニットはその公開インターフェース（別名「公開API」または「表面積」）をのみを使ってテストされます。これはブラックボックステストと呼ばれます。ブラックボックステストは不安定さの少ないテストにつながります、なぜならユニットの実装の詳細はユニットの公開APIよりも長い間変更されがちだからです。もしあなたがホワイトボックステストを使うのであれば、ホワイトボックステストではテストは実装の詳細を把握しているのですが、実装の詳細へのあらゆる変更はテストを壊す可能性があります、たとえ公開APIが期待される通りに機能し続けているとしても。言い換えれば、ホワイトボックステストは無駄な再作業につながります。
