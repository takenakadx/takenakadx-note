**********
sphinx
**********

`sphinx <https://www.sphinx-doc.org/ja/>`_ はpythonで動くドキュメント生成ツールである.

本ドキュメントもsphinxによって作成されている

sphinxは `reStructuredtext <https://www.sphinx-doc.org/ja/1.3/rest.html>`_ によって書かれたドキュメントを見やすくするツールである

.. sphinx_how-to-start:

始め方
****************

インストール方法
=================================

sphinx自体のインストールは `pip` で可能 ::

    $ pip install sphinx

sphinx-autobuildもインストールしておくとよい ::

    $ pip install sphinx-autobuild

ドキュメント作成
==================

適当なディレクトリを作成しsphinx-quickstartコマンドで始める ::

    $ sphinx-quickstart

ビルド方法
===============

ここではhtmlにビルドする方法を説明する

makeを使う場合
-----------------

make.batがあるフォルダで以下を実行 ::

    $ make html

autobuildを使う場合
--------------------

sphinx-autobuildをインストールしておき以下を実行 ::

    $ sphinx-autobuild <作業ディレクトリ> <ビルド先のフォルダ名>

.. sphinx_how-to-write

主な **ReStructuredText** の書き方
************************************

ReStructuredTextの文法を簡単に解説する。

セクション
==========

::

    = - ` : . ' " ~ ^ _ * + #

これらの文字を使う事でセクションが作成できる

::

    セクション(レベル2)
    =====================

    レベル3
    ========

    レベル4
    --------

    レベル5
    ^^^^^^^^

**出力例**

セクション(レベル2)
=====================

レベル3
========

レベル4
--------

レベル5
^^^^^^^^



強調
====

======== =========== ============ 
_          使用例      書き方       
======== =========== ============
強調     *文字列*    \*で囲む     
強い強調 **文字列**  \*\*で囲む   
コード   ``文字列``  \`\`で囲む   
======== =========== ============



ラインブロック
====

改行をそのまま表示したい場合には、ラインブロックを使います。

.. code-block:: rst

    | これらの行は、
    | ソースファイルと同じように
    | 改行されます。


| これらの行は、
| ソースファイルと同じように
| 改行されます。



リスト
==============

\*、+、-を使って項目を並べると番号なしリストになります。


::

    * 項目1
    * 項目2
    * 項目3


**出力例**

* 項目1
* 項目2
* 項目3

数字を使えば番号付きリストとなる #を利用して番号の自動振り分けもできる

.. code-block:: rst

    1. 項目1
    2. 項目2
    3. 項目3

    #. 項目1
    #. 項目2
    #. 項目3


1. 項目1
2. 項目2
3. 項目3

#. 項目1
#. 項目2
#. 項目3


コードブロック
===============
\:\:のあと１行開けてから１段インデントして書く。

::

    ふつうの文章 ::

        コードブロック

ふつうの文章 ::

    コードブロック


code-blockディレクティブを使うこともできる ::

    .. code-block:: python

        import sys

        print sys.path

.. code-block:: python

    import sys

    print sys.path

ラベルと参照
============

 **ラベル** をつけておき、そこに対してrefでリンクを作ることができます。

.. code-block:: rst

    .. _sample-label:

    タイトル
    =========
    文章

    :ref:`sample-label` を参照


以下はサンプルです。

.. _sample-label:

タイトル
--------
文章

:ref:`sample-label` を参照


他のドキュメントへの参照
========================

別の文書へのリンクを作りたい場合には、次のように書く

.. code-block:: rst

    :doc:`markdown`


:doc:`markdown`


リンク
========
::

    * `github <https://google.com>`_
    * google-link_

    .. _google-link: http://google.com/


#. `hello google!`_ と書いておいて、
   あとから \.\. \_`hello google!`: URL とするとリンクになる。
#. `google! <https://google.com/>`_ とするとリンクになる。

.. _`hello google!`: https://google.com


ダウンロード用のリンク
======================

::

    :download:`このファイル <markdown.rst>`


:download:`このファイル <./markdown.rst>`


画像
====

.. code-block:: rst

    .. image:: sample.png

.. image:: sample.png




テーブル
========

テーブル1
----------

.. code-block:: rst

    ======= ====== ======
    col1    col2   col3
    ======= ====== ======
    row1    a      b
    row2    a      b
    row3    a      b
    ======= ====== ======


======= ====== ======
col1    col2   col3
======= ====== ======
row1    a      b
row2    a      b
row3    a      b
======= ====== ======


テーブル2
----------

.. code-block:: rst

    +------------------------+------------+----------+----------+
    | Header row, column 1   | Header 2   | Header 3 | Header 4 |
    | (header rows optional) |            |          |          |
    +========================+============+==========+==========+
    | body row 1, column 1   | column 2   | column 3 | column 4 |
    +------------------------+------------+----------+----------+
    | body row 2             | ...        | ...      |          |
    +------------------------+------------+----------+----------+


+------------------------+------------+----------+----------+
| Header row, column 1   | Header 2   | Header 3 | Header 4 |
| (header rows optional) |            |          |          |
+========================+============+==========+==========+
| body row 1, column 1   | column 2   | column 3 | column 4 |
+------------------------+------------+----------+----------+
| body row 2             | ...        | ...      |          |
+------------------------+------------+----------+----------+

     
注釈
====

ノート

.. code-block:: rst

    .. note::

        これは注釈です！

.. note::
    
    これは注釈です！

警告

.. code-block:: rst

    .. warning::

        これは警告です！

.. warning::
    
    これは警告です！

索引
====
indexディレクティブを設定することで、索引を作ることができます。

.. index:: Sample


.. index::
    pair: Sample; Sphinx


.. code-block:: rst
    
    .. index:: Sample
    
    .. index::
        pair: Sample; Sphinx
    

* :ref:`genindex`


他のファイルのインクルード
==========================
ファイルをreStructuredTextとして取り込みたい場合には includeを使用します。

.. code-block:: rst

    .. include:: markdown.rst


.. include:: markdown.rst


ファイルを引用として取り込みたい場合には、literalincludeを使用します。

.. code-block:: rst

    .. literalinclude:: markdown.rst
        :language: rst
        :linenos:


.. literalinclude:: markdown.rst
    :language: rst
    :linenos:



参考
====
* `sphinxでの文章の書き方 <https://planset-study-sphinx.readthedocs.io/ja/latest/04.html>`_
