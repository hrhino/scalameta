We use macro annotations to generate swaths of boilerplate that are required for our abstract syntax trees
to be efficient and convenient. Here's the code that we write in [Trees.scala](/scalameta/Trees.scala):

```
@ast class If(cond: Term, thenp: Term, elsep: Term = Lit.Unit()) extends Term
```

Here's the code generated by the `@ast` macro annotation:

```
@_root_.org.scalameta.ast.internal.astClass @_root_.org.scalameta.adt.Internal.leafClass final class If private (
  protected val internalPrototype: If,
  protected val internalParent: _root_.scala.meta.Tree,
  protected val internalScratchpads: _root_.scala.collection.immutable.Map[_root_.scala.meta.semantic.Host, _root_.scala.collection.immutable.Seq[Any]]
)(
  private var _cond: Term,
  private var _thenp: Term,
  private var _elsep: Term,
  @_root_.org.scalameta.ast.trivia @_root_.org.scalameta.ast.auto private var _hasElsep: _root_.scala.Boolean
) extends Term with _root_.scala.Product {
  private[meta] def internalCopy(prototype: _root_.scala.meta.Tree = this, parent: _root_.scala.meta.Tree = internalParent, scratchpads: _root_.scala.collection.immutable.Map[_root_.scala.meta.semantic.Host, _root_.scala.collection.immutable.Seq[Any]] = internalScratchpads): ThisType = new ThisType(prototype.asInstanceOf[ThisType], parent, scratchpads)(_root_.org.scalameta.ast.internal.initField(this._cond), _root_.org.scalameta.ast.internal.initField(this._thenp), _root_.org.scalameta.ast.internal.initField(this._elsep), _root_.org.scalameta.ast.internal.initField(this._hasElsep));
  def parent: _root_.scala.Option[_root_.scala.meta.Tree] = if (internalParent.$bang$eq(null))
    _root_.scala.Some(internalParent)
  else
    _root_.scala.None;
  def cond: Term = {
    _root_.org.scalameta.ast.internal.loadField(this._cond);
    this._cond
  };
  def thenp: Term = {
    _root_.org.scalameta.ast.internal.loadField(this._thenp);
    this._thenp
  };
  def elsep: Term = {
    _root_.org.scalameta.ast.internal.loadField(this._elsep);
    this._elsep
  };
  def hasElsep: _root_.scala.Boolean = {
    _root_.org.scalameta.ast.internal.loadField(this._hasElsep);
    this._hasElsep
  };
  def copy(cond: Term = this.cond, thenp: Term = this.thenp, elsep: Term = this.elsep): ThisType = If.apply(cond, thenp, elsep);
  override type ThisType = If;
  override def $tag: Int = $tag;
  override def productPrefix: _root_.scala.Predef.String = _root_.org.scalameta.ast.internal.productPrefix[ThisType];
  override def productArity: _root_.scala.Int = 3;
  override def productElement(n: _root_.scala.Int): Any = n match {
    case 0 => this.cond
    case 1 => this.thenp
    case 2 => this.elsep
    case _ => throw new _root_.scala.IndexOutOfBoundsException(n.toString)
  };
  override def productIterator: _root_.scala.Iterator[_root_.scala.Any] = _root_.scala.runtime.ScalaRunTime.typedProductIterator(this);
  override def canEqual(that: _root_.scala.Any): _root_.scala.Boolean = that.isInstanceOf[ThisType];
  override def equals(that: _root_.scala.Any): _root_.scala.Boolean = this.eq(that.asInstanceOf[AnyRef]);
  override def hashCode: _root_.scala.Int = _root_.java.lang.System.identityHashCode(this)
}
@_root_.org.scalameta.ast.internal.astCompanion @_root_.org.scalameta.adt.Internal.leafCompanion object If {
  def $tag: _root_.scala.Int = _root_.org.scalameta.adt.Internal.calculateTag[ThisType];
  def apply(cond: Term, thenp: Term, elsep: Term = null): If = {
    def internal(cond: Term, thenp: Term, elsep: Term, @new _root_.org.scalameta.ast.trivia() @new _root_.org.scalameta.ast.auto() hasElsep: _root_.scala.Boolean): If = {
      _root_.org.scalameta.adt.Internal.hierarchyCheck[If];
      _root_.org.scalameta.adt.Internal.nullCheck(cond);
      _root_.org.scalameta.adt.Internal.nullCheck(thenp);
      _root_.org.scalameta.adt.Internal.nullCheck(elsep);
      _root_.org.scalameta.adt.Internal.nullCheck(hasElsep);
      _root_.org.scalameta.adt.Internal.emptyCheck(cond);
      _root_.org.scalameta.adt.Internal.emptyCheck(thenp);
      _root_.org.scalameta.adt.Internal.emptyCheck(elsep);
      _root_.org.scalameta.adt.Internal.emptyCheck(hasElsep);
      val node = new If(null, null, _root_.scala.collection.immutable.Map())(_root_.org.scalameta.ast.internal.initParam(cond), _root_.org.scalameta.ast.internal.initParam(thenp), _root_.org.scalameta.ast.internal.initParam(elsep), _root_.org.scalameta.ast.internal.initParam(hasElsep));
      _root_.org.scalameta.ast.internal.storeField(node._cond, cond);
      _root_.org.scalameta.ast.internal.storeField(node._thenp, thenp);
      _root_.org.scalameta.ast.internal.storeField(node._elsep, elsep);
      _root_.org.scalameta.ast.internal.storeField(node._hasElsep, hasElsep);
      node
    };
    internal(cond, thenp, if (elsep.$bang$eq(null))
      elsep
    else
      Lit.Unit(), elsep.$bang$eq(null))
  };
  def unapply(x: If): Option[scala.Tuple3[Term, Term, Term]] = if (x.$eq$eq(null))
    _root_.scala.None
  else
    _root_.scala.Some(scala.Tuple3(x.cond, x.thenp, x.elsep))
}
```

Here's the same code after typechecking with helper def macros expanded:

```
@org.scalameta.ast.internal.astClass @org.scalameta.adt.Internal.leafClass final class If extends AnyRef with scala.meta.syntactic.ast.Term with Product {
  <paramaccessor> private[this] val internalPrototype: scala.meta.syntactic.ast.Term.If = _;
  <stable> <accessor> <paramaccessor> protected def internalPrototype: scala.meta.syntactic.ast.Term.If = If.this.internalPrototype;
  <paramaccessor> private[this] val internalParent: scala.meta.Tree = _;
  <stable> <accessor> <paramaccessor> protected def internalParent: scala.meta.Tree = If.this.internalParent;
  <paramaccessor> private[this] val internalScratchpads: scala.collection.immutable.Map[scala.meta.semantic.Host,scala.collection.immutable.Seq[Any]] = _;
  <stable> <accessor> <paramaccessor> protected def internalScratchpads: scala.collection.immutable.Map[scala.meta.semantic.Host,scala.collection.immutable.Seq[Any]] = If.this.internalScratchpads;
  <paramaccessor> private[this] var _cond: scala.meta.syntactic.ast.Term = _;
  <accessor> <paramaccessor> private def _cond: scala.meta.syntactic.ast.Term = If.this._cond;
  <accessor> <paramaccessor> private def _cond_=(x$1: scala.meta.syntactic.ast.Term): Unit = If.this._cond = x$1;
  <paramaccessor> private[this] var _thenp: scala.meta.syntactic.ast.Term = _;
  <accessor> <paramaccessor> private def _thenp: scala.meta.syntactic.ast.Term = If.this._thenp;
  <accessor> <paramaccessor> private def _thenp_=(x$1: scala.meta.syntactic.ast.Term): Unit = If.this._thenp = x$1;
  <paramaccessor> private[this] var _elsep: scala.meta.syntactic.ast.Term = _;
  <accessor> <paramaccessor> private def _elsep: scala.meta.syntactic.ast.Term = If.this._elsep;
  <accessor> <paramaccessor> private def _elsep_=(x$1: scala.meta.syntactic.ast.Term): Unit = If.this._elsep = x$1;
  <paramaccessor> private[this] var _hasElsep: Boolean = _;
  <accessor> <paramaccessor> private def _hasElsep: Boolean = If.this._hasElsep;
  <accessor> <paramaccessor> private def _hasElsep_=(x$1: Boolean): Unit = If.this._hasElsep = x$1;
  private def <init>(internalPrototype: scala.meta.syntactic.ast.Term.If, internalParent: scala.meta.Tree, internalScratchpads: scala.collection.immutable.Map[scala.meta.semantic.Host,scala.collection.immutable.Seq[Any]])(_cond: scala.meta.syntactic.ast.Term, _thenp: scala.meta.syntactic.ast.Term, _elsep: scala.meta.syntactic.ast.Term, @org.scalameta.ast.trivia @org.scalameta.ast.auto _hasElsep: Boolean): scala.meta.syntactic.ast.Term.If = {
    If.super.<init>();
    ()
  };
  private[meta] def internalCopy(prototype: scala.meta.Tree = this, parent: scala.meta.Tree = If.this.internalParent, scratchpads: scala.collection.immutable.Map[scala.meta.semantic.Host,scala.collection.immutable.Seq[Any]] = If.this.internalScratchpads): If.this.ThisType = new If.this.ThisType(prototype.asInstanceOf[If.this.ThisType], parent, scratchpads)((null: scala.meta.syntactic.ast.Term), (null: scala.meta.syntactic.ast.Term), (null: scala.meta.syntactic.ast.Term), (this._hasElsep: Boolean));
  override <synthetic> def internalCopy$default$1: scala.meta.Tree = this;
  override <synthetic> def internalCopy$default$2: scala.meta.Tree = If.this.internalParent;
  override <synthetic> def internalCopy$default$3: scala.collection.immutable.Map[scala.meta.semantic.Host,scala.collection.immutable.Seq[Any]] = If.this.internalScratchpads;
  def parent: Option[scala.meta.Tree] = if (If.this.internalParent.!=(null))
    scala.Some.apply[scala.meta.Tree](If.this.internalParent)
  else
    scala.None;
  def cond: scala.meta.syntactic.ast.Term = {
    (if (this._cond.==(null))
      {
        scala.Predef.require(this.internalPrototype.!=(null), "internal error when initializing If.cond");
        this._cond_=({
          <artifact> val qual$19: scala.meta.syntactic.ast.Term = this.internalPrototype.cond;
          <artifact> val x$79: scala.meta.syntactic.ast.Term = this.internalPrototype.cond;
          <artifact> val x$80: scala.meta.syntactic.ast.Term.If = this;
          <artifact> val x$81: Map[scala.meta.semantic.Host,scala.collection.immutable.Seq[Any]] @scala.reflect.internal.annotations.uncheckedBounds = qual$19.internalCopy$default$3;
          qual$19.internalCopy(x$79, x$80, x$81)
        })
      }
    else
      (): Unit);
    this._cond
  };
  def thenp: scala.meta.syntactic.ast.Term = {
    (if (this._thenp.==(null))
      {
        scala.Predef.require(this.internalPrototype.!=(null), "internal error when initializing If.thenp");
        this._thenp_=({
          <artifact> val qual$20: scala.meta.syntactic.ast.Term = this.internalPrototype.thenp;
          <artifact> val x$82: scala.meta.syntactic.ast.Term = this.internalPrototype.thenp;
          <artifact> val x$83: scala.meta.syntactic.ast.Term.If = this;
          <artifact> val x$84: Map[scala.meta.semantic.Host,scala.collection.immutable.Seq[Any]] @scala.reflect.internal.annotations.uncheckedBounds = qual$20.internalCopy$default$3;
          qual$20.internalCopy(x$82, x$83, x$84)
        })
      }
    else
      (): Unit);
    this._thenp
  };
  def elsep: scala.meta.syntactic.ast.Term = {
    (if (this._elsep.==(null))
      {
        scala.Predef.require(this.internalPrototype.!=(null), "internal error when initializing If.elsep");
        this._elsep_=({
          <artifact> val qual$21: scala.meta.syntactic.ast.Term = this.internalPrototype.elsep;
          <artifact> val x$85: scala.meta.syntactic.ast.Term = this.internalPrototype.elsep;
          <artifact> val x$86: scala.meta.syntactic.ast.Term.If = this;
          <artifact> val x$87: Map[scala.meta.semantic.Host,scala.collection.immutable.Seq[Any]] @scala.reflect.internal.annotations.uncheckedBounds = qual$21.internalCopy$default$3;
          qual$21.internalCopy(x$85, x$86, x$87)
        })
      }
    else
      (): Unit);
    this._elsep
  };
  def hasElsep: Boolean = {
    (<empty>: Unit);
    this._hasElsep
  };
  def copy(cond: scala.meta.syntactic.ast.Term = this.cond, thenp: scala.meta.syntactic.ast.Term = this.thenp, elsep: scala.meta.syntactic.ast.Term = this.elsep): If.this.ThisType = Term.this.If.apply(cond, thenp, elsep);
  <synthetic> def copy$default$1: scala.meta.syntactic.ast.Term = this.cond;
  <synthetic> def copy$default$2: scala.meta.syntactic.ast.Term = this.thenp;
  <synthetic> def copy$default$3: scala.meta.syntactic.ast.Term = this.elsep;
  override type ThisType = scala.meta.syntactic.ast.Term.If;
  override def $tag: Int = Term.this.If.$tag;
  override def productPrefix: String = ("Term.If": String);
  override def productArity: Int = 3;
  override def productElement(n: Int): Any = n match {
    case 0 => this.cond
    case 1 => this.thenp
    case 2 => this.elsep
    case _ => throw new scala.`package`.IndexOutOfBoundsException(n.toString())
  };
  override def productIterator: Iterator[Any] = scala.runtime.ScalaRunTime.typedProductIterator[Nothing](this);
  override def canEqual(that: Any): Boolean = that.isInstanceOf[If.this.ThisType];
  override def equals(that: Any): Boolean = this.eq(that.asInstanceOf[AnyRef]);
  override def hashCode: Int = java.lang.System.identityHashCode(this)
};
@@<?> @@<?> object If extends scala.AnyRef {
  def <init>(): scala.meta.syntactic.ast.Term.If.type = {
    If.super.<init>();
    ()
  };
  def $tag: Int = 18;
  def apply(cond: scala.meta.syntactic.ast.Term, thenp: scala.meta.syntactic.ast.Term, elsep: scala.meta.syntactic.ast.Term = null): scala.meta.syntactic.ast.Term.If = {
    def internal(cond: scala.meta.syntactic.ast.Term, thenp: scala.meta.syntactic.ast.Term, elsep: scala.meta.syntactic.ast.Term, @org.scalameta.ast.trivia @org.scalameta.ast.auto hasElsep: Boolean): scala.meta.syntactic.ast.Term.If = {
      <empty>;
      ({
        val result$macro$104: Boolean = cond.!=(null);
        if (result$macro$104)
          scala.Tuple2.apply[Boolean, scala.collection.immutable.Nil.type](true, immutable.this.Nil)
        else
          scala.Tuple2.apply[Boolean, List[String]](false, immutable.this.List.apply[String]("cond is equal to null"))
      } match {
        case (_1: Boolean, _2: List[String])(Boolean, List[String])(true, _) => ()
        case (_1: Boolean, _2: List[String])(Boolean, List[String])(false, (failures$macro$103 @ _)) => {
          org.scalameta.invariants.InvariantFailedException.raise("cond.!=(null)", failures$macro$103, scala.collection.immutable.Map.apply[String, scala.meta.syntactic.ast.Term](scala.Tuple2.apply[String, scala.meta.syntactic.ast.Term]("cond", cond)));
          ()
        }
      }: Unit);
      ({
        val result$macro$106: Boolean = thenp.!=(null);
        if (result$macro$106)
          scala.Tuple2.apply[Boolean, scala.collection.immutable.Nil.type](true, immutable.this.Nil)
        else
          scala.Tuple2.apply[Boolean, List[String]](false, immutable.this.List.apply[String]("thenp is equal to null"))
      } match {
        case (_1: Boolean, _2: List[String])(Boolean, List[String])(true, _) => ()
        case (_1: Boolean, _2: List[String])(Boolean, List[String])(false, (failures$macro$105 @ _)) => {
          org.scalameta.invariants.InvariantFailedException.raise("thenp.!=(null)", failures$macro$105, scala.collection.immutable.Map.apply[String, scala.meta.syntactic.ast.Term](scala.Tuple2.apply[String, scala.meta.syntactic.ast.Term]("thenp", thenp)));
          ()
        }
      }: Unit);
      ({
        val result$macro$108: Boolean = elsep.!=(null);
        if (result$macro$108)
          scala.Tuple2.apply[Boolean, scala.collection.immutable.Nil.type](true, immutable.this.Nil)
        else
          scala.Tuple2.apply[Boolean, List[String]](false, immutable.this.List.apply[String]("elsep is equal to null"))
      } match {
        case (_1: Boolean, _2: List[String])(Boolean, List[String])(true, _) => ()
        case (_1: Boolean, _2: List[String])(Boolean, List[String])(false, (failures$macro$107 @ _)) => {
          org.scalameta.invariants.InvariantFailedException.raise("elsep.!=(null)", failures$macro$107, scala.collection.immutable.Map.apply[String, scala.meta.syntactic.ast.Term](scala.Tuple2.apply[String, scala.meta.syntactic.ast.Term]("elsep", elsep)));
          ()
        }
      }: Unit);
      <empty>;
      <empty>;
      <empty>;
      <empty>;
      <empty>;
      val node: scala.meta.syntactic.ast.Term.If = new Term.this.If(null, null, scala.collection.immutable.Map.apply[scala.meta.semantic.Host, Nothing]())((null: scala.meta.syntactic.ast.Term), (null: scala.meta.syntactic.ast.Term), (null: scala.meta.syntactic.ast.Term), (hasElsep: Boolean));
      (node._cond_=(cond.internalCopy(cond, node, cond.internalCopy$default$3)): Unit);
      (node._thenp_=(thenp.internalCopy(thenp, node, thenp.internalCopy$default$3)): Unit);
      (node._elsep_=(elsep.internalCopy(elsep, node, elsep.internalCopy$default$3)): Unit);
      (<empty>: Unit);
      node
    };
    internal(cond, thenp, if (elsep.!=(null))
      elsep
    else
      Lit.Unit.apply(), elsep.!=(null))
  };
  <synthetic> def apply$default$3: scala.meta.syntactic.ast.Term = null;
  def unapply(x: scala.meta.syntactic.ast.Term.If): Option[(scala.meta.syntactic.ast.Term, scala.meta.syntactic.ast.Term, scala.meta.syntactic.ast.Term)] = if (x.==(null))
    scala.None
  else
    scala.Some.apply[(scala.meta.syntactic.ast.Term, scala.meta.syntactic.ast.Term, scala.meta.syntactic.ast.Term)](scala.Tuple3.apply[scala.meta.syntactic.ast.Term, scala.meta.syntactic.ast.Term, scala.meta.syntactic.ast.Term](x.cond, x.thenp, x.elsep))
};
```